meadowmachine
========

(max) complex cascading counter, with iterative pattern arrays

october 2014, by Raymond Weitekamp, forked from meadowphysics by tehn@monome.org, inspired by Dan Trueman's Clapping Machine Music Variations ( http://plork.princeton.edu/PLOrk-Spring2010/ | http://dtrueman.mycpanel.princeton.edu/cmmv.pdf )

still relies on teletype: https://github.com/monome/teletype

INSTRUCTIONS:

set countdown positions. when they hit 0 (leftmost) - a trigger occurs.

on trigger, a few things happen:

1. event is generated. currently this is hard-mapped to teletype (another app).
2. (a) 'default rule': count is reset. (b) if the rule is anything other than 'default' [1] or 'save' [8], the count is reset to the next number in the pattern array (see rules)
3. linked rows have their positions subtracted by one.
4. a "rule" is executed. the meadowmachine rules allow various patterns of counts from the pattern array.

only the top row is constantly triggered by the metro.

to have other rows count down, you need to link them.

holding down the leftmost keys shows the output linking for each row.

so, by pushing the topleft key, you'll see the rows that will get subtracted when row 0 hits 0. by default none are selected. while holding the top-left key, push the middle of other rows to toggle them.

you can have multiple rows triggering the same row. a row cannot trigger itself. it's quite easy to create strange evolving polyrhythmic counting.

set a rule by holding down the two leftmost keys, per row. select the rule by vertically on the right side of the grid-- the icon will change. select the destination row for the rule execution in the middle of the grid.

the rules are different than meadowphysics. instead of operating on the position directly, they operate on the index of the pattern array: 
1. 'default' - no change
2. increment array index
3. decrement array index
4. set to max value in the array
5. set to min value in the array
6. random value from array
7. random walk of the array index
8. recall last pressed - no change

for example, on row 0, a rule of random with destination row 0: on each trigger, a random new starting position will be chosen from the positions listed in the array.

for example, on row 1, a rule of increment destination row 0: on each trigger of row 1, row 0 will get reset to the next position in the array.

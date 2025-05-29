Count how many loops a variable is on.

A => +B, B => +C, C => +A, C => -A will be treated as 2 loops: [1,2,3] and [1,2,4]. Each variable will be treated as being on 2 loops.

Takes a CausalLoopPM or a CausalLoopPol, and a Symbol.  Throws an error if that Symbol is the name for more than one variable.

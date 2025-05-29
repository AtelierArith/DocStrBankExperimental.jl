Count how many loops a variable is on, ignoring when two vertices have more than one edge between them.

A => +B, B => +C, C => +A, C => -A will be treated as 1 loop.

Takes a CausalLoopPM or a CausalLoopPol, and a Symbol.  Throws an error if that Symbol is the name for more than one variable.

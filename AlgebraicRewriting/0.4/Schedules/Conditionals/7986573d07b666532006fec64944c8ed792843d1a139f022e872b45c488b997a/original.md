A primitive box in a NestedDWD which does not change the state but redirects it  out of one of n wires. 

It contains a function (A->X) -> ℝⁿ. This optionally depends on the internal  state. This weights probability for n outports, conditional on the status of an  ACSet. If the function just depends on X rather than the whole morphism,  `withagent` is `false`. If the function does not depend on the internal state  (assumed to be true iff initial state is `nothing`), then `withstate` is `false`.

The state and update function are by default trivial.

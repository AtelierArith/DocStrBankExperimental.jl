```
deposit!(w::AbstractDVec, add, val, parent::Pair)
```

Add `val` into `w` at address `add`, taking into account initiator rules if applicable. `parent` contains the `address => value` pair from which the pair `add => val` was created. [`InitiatorDVec`](@ref Main.DictVectors.InitiatorDVec) can intercept this and add its own functionality.

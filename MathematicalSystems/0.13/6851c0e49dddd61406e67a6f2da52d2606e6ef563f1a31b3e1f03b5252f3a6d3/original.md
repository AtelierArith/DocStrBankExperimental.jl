```
AbstractInput
```

Abstract supertype for all input types.

### Notes

The input types defined here implement an iterator interface, such that other methods can build upon the behavior of inputs which are either constant or varying.

Iteration is supported with an index number called *iterator state*. The iteration function `Base.iterate` takes and returns a tuple (`input`, `state`), where `input` represents the value of the input, and `state` is an index which counts the number of times this iterator was called.

A convenience function `nextinput(input, n)` is also provided and it returns the first `n` elements of `input`.

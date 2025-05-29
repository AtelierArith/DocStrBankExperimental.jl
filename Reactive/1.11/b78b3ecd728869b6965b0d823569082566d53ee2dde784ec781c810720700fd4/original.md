```
foldp(f, init, inputs...)
```

[Fold](http://en.wikipedia.org/wiki/Fold_(higher-order_function)) over past values.

Accumulate a value as the input signals change. `init` is the initial value of the accumulator. `f` should take `1 + length(inputs)` arguments: the first is the current accumulated value and the rest are the current input signal values. `f` will be called when one or more of the `inputs` updates. It should return the next accumulated value.

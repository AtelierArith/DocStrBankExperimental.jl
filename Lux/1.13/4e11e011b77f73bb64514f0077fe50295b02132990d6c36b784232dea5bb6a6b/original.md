```
RepeatedLayer(model; repeats::Val = Val(10), input_injection::Val = Val(false))
```

Iteratively applies `model` for `repeats` number of times. The initial input is passed into the model repeatedly if `input_injection = Val(true)`. This layer unrolls the computation, however, semantically this is same as:

  * `input_injection = Val(false)`

```julia
res = x
for i in 1:repeats
    res, st = model(res, ps, st)
end
```

  * `input_injection = Val(true)`

```julia
res = x
for i in 1:repeats
    res, st = model((res, x), ps, st)
end
```

It is expected that `repeats` will be a reasonable number below `20`, beyond that compile times for gradients might be unreasonably high.

## Arguments

  * `model` must be an `AbstractLuxLayer`

## Keyword Arguments

  * `repeats`: Number of times to apply the model
  * `input_injection`: If `true`, then the input is passed to the model along with the output

# Extended Help

## Inputs

  * `x`: Input as described above

## Returns

  * Output is computed by as described above
  * Updated state of the `model`

## Parameters

  * Parameters of `model`

## States

  * State of `model`

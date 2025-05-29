```
Stacked(bs)
Stacked(bs, ranges)
stack(bs::Bijector...)
```

A `Bijector` which stacks bijectors together which can then be applied to a vector where `bs[i]::Bijector` is applied to `x[ranges[i]]::UnitRange{Int}`.

# Arguments

  * `bs` can be either a `Tuple` or an `AbstractArray` of 0- and/or 1-dimensional bijectors

      * If `bs` is a `Tuple`, implementations are type-stable using generated functions
      * If `bs` is an `AbstractArray`, implementations are *not* type-stable and use iterative methods
  * `ranges` needs to be an iterable consisting of `UnitRange{Int}`

      * `length(bs) == length(ranges)` needs to be true.

# Examples

```
b1 = Logit(0.0, 1.0)
b2 = identity
b = stack(b1, b2)
b([0.0, 1.0]) == [b1(0.0), 1.0]  # => true
```

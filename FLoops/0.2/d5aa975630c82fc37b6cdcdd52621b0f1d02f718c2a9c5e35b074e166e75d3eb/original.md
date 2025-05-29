```
@reduce() do (acc₁ [= init₁]; x₁), ..., (accₙ [= initₙ]; xₙ)
    ...
end
@reduce(acc₁ ⊗₁= x₁, ..., accₙ ⊗ₙ= xₙ)
@reduce(acc₁ .⊗₁= x₁, ..., accₙ .⊗ₙ= xₙ)
@reduce(acc₁ = ⊗₁(init₁, x₁), ..., accₙ = ⊗ₙ(initₙ, xₙ))
@reduce(acc₁ .= (⊗₁).(init₁, x₁), ..., accₙ = (⊗ₙ).(initₙ, xₙ))
```

Declare how accumulators are updated in the sequential basecase and how the resulting accumulators from two basecases are combined.

The arguments `accᵢ` and `xᵢ` must be symbols except for `xᵢ` of the last three forms in which an expression can be used at `xᵢ`.

In the first form,

```julia
function ((acc₁, acc₂, ..., accₙ), (x₁, x₂, ..., xₙ))
    ...  # body of the `do` block
    return (acc₁, acc₂, ..., accₙ)
end
```

should be an associative function.

In the last three forms, every binary operation `⊗ᵢ` should be an associative function.

If `initᵢ` is specified, the tuple `(init₁, init₂, ..., initₙ)` should be the identify of the related associative function.  `accᵢ = initᵢ` is evaluated for each basecase (each `Task`) in the beginning.

Consider a loop with the following form

```julia
@floop for ...
    # code computing (x₁, x₂, ..., xₙ)
    @reduce() do (acc₁ = init₁; x₁), ..., (accₙ = initₙ; xₙ)
        # code updating (acc₁, acc₂, ..., accₙ) using (x₁, x₂, ..., xₙ)
    end
end
```

This is converted to

```julia
acc₁ = init₁
...
accₙ = initₙ
for ...
    # code computing (x₁, x₂, ..., xₙ)
    # code updating (acc₁, acc₂, ..., accₙ) using (x₁, x₂, ..., xₙ)
end
```

for computing `(acc₁, acc₂, ..., accₙ)` of each basecase.  The accumulators `accᵢ` of two basecases are combined using "code updating `(acc₁, acc₂, ..., accₙ)` using `(x₁, x₂, ..., xₙ)`" where `(x₁, x₂, ..., xₙ)` are replaced with `(acc₁, acc₂, ..., accₙ)` of the next basecase.  Note that "code computing `(x₁, x₂, ..., xₙ)`" is not used for combining the basecases.

# Examples

```julia
@reduce() do (vmax=-Inf; v), (imax=0; i)
    if isless(vmax, v)
        vmax = v
        imax = i
    end
end

@reduce(s += y, p *= y)

@reduce(xs = append!!(EmptyVector(), x), ys = append!!(EmptyVector(), y))
```

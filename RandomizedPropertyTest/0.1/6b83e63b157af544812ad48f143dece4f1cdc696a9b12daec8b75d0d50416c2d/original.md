```
Disk{T,z₀,r}
```

Represents a Disk of radius `r and center`z₀`in the set`T`(boundary excluded).`r`should be nonnegative. Both`z`and`r` should be finite and non-NaN.

The type is used to generate variables `x` of type `T` such that (abs(x-z) < r) for the `@quickcheck` macro:

```
julia> @quickcheck (typeof(x) == ComplexF16 && abs(x-2im) < 3) (x :: Disk{Complex{Float16}, 2im, 3})
true
```

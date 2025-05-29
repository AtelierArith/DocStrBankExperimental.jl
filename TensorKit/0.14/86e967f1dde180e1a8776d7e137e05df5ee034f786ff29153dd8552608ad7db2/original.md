```
flip(t::AbstractTensorMap, I) -> t′::AbstractTensorMap
```

Return a new tensor that is isomorphic to `t` but where the arrows on the indices `i` that satisfy `i ∈ I` are flipped, i.e. `space(t′, i) = flip(space(t, i))`.

!!! note
    The isomorphism that `flip` applies to each of the indices `i ∈ I` is such that flipping two indices that are afterwards contracted within an `@tensor` contraction will yield the same result as without flipping those indices first. However, `flip` is not involutory, i.e. `flip(flip(t, I), I) != t` in general. To obtain the original tensor, one can use the `inv` keyword, i.e. it holds that `flip(flip(t, I), I; inv=true) == t`.


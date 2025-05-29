```
*(g::Perm, h::Perm)
```

Return the composition $h ∘ g$ of two permutations.

This corresponds to the action of permutation group on the set `[1..n]` **on the right** and follows the convention of GAP.

If `g` and `h` are parametrized by different types, the result is promoted accordingly.

# Examples

```jldoctest
julia> Perm([2,3,1,4])*Perm([1,3,4,2]) # (1,2,3)*(2,3,4)
(1,3)(2,4)
```

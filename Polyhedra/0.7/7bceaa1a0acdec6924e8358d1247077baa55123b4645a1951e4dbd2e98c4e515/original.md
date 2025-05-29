```
fixandeliminate(p::HRep{T}, I, v)
```

Fix the variables with indices in `I` to the corresponding value in `v`. This is equivalent to doing the following:

```julia
function ei(i)
    a = zeros(T, fulldim(p))
    a[i] = one(T)
    a
end
eliminate(p ∩ HyperPlane(ei(I[1]), v[1]) ∩ ... ∩ HyperPlane(ei(I[n]), v[n]))
```

where `n` is the length of `I` (and `v`), but it is much more efficient. The code above does a polyhedral projection while this function simply replaces each halfspace `⟨a, x⟩ ≤ β` (resp. each hyperplane `⟨a, x⟩ = β`) by the halfspace `⟨a_J, x⟩ ≤ β - ⟨a_I, v⟩` (resp. the hyperplane `⟨a_J, x⟩ = β - ⟨a_I, v⟩`) where `J = setdiff(1:fulldim(p), I)`.

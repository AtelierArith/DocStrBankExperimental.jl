```
fubini_study(v::PVector{<:Number,N}, w::PVector{<:Number, N})
```

Compute the Fubini-Study distance between `v` and `w` for each component `vᵢ` and `wᵢ`. This is defined as $\arccos|⟨vᵢ,wᵢ⟩|$.

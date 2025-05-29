```
update!(
    μtuner::MuTunerLogger{T,S},
    n::Number, N²::Number, s::S=one(S)
) where {T<:AbstractFloat, S<:Number}
```

Update the chemical potential given new measurements of the particle density `n`, the total particle number squared `N²`, and the sign `s`.

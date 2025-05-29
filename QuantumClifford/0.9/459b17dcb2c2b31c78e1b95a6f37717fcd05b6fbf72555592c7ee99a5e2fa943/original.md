Measure a qubit in the Z basis and reset to the |0⟩ state.

!!! warning "It does not trace out the qubit!"
    As described below there is a difference between measuring the qubit (followed by setting it to a given known state) and "tracing out" the qubit. By reset here we mean "measuring and setting to a known state", not "tracing out".


```jldoctest
julia> s = MixedDestabilizer(S"XXX ZZI IZZ") # |000⟩+|111⟩
𝒟ℯ𝓈𝓉𝒶𝒷
+ Z__
+ _X_
+ __X
𝒮𝓉𝒶𝒷━
+ XXX
+ ZZ_
+ Z_Z

julia> traceout!(copy(s), 1) # = I⊗(|00⟩⟨00| + |11⟩⟨11|)
𝒟ℯ𝓈𝓉𝒶𝒷
+ _X_
𝒳ₗ━━━
+ _XX
+ Z__
𝒮𝓉𝒶𝒷━
+ _ZZ
𝒵ₗ━━━
+ Z_Z
+ XXX

julia> projectZ!(traceout!(copy(s), 1), 1)[1] # = |000⟩⟨000|+|011⟩⟨011| or |100⟩⟨100|+|111⟩⟨111| (use projectZrand! to actually get a random result)
𝒟ℯ𝓈𝓉𝒶𝒷
+ _X_
+ XXX
𝒳ₗ━━━
+ _XX
𝒮𝓉𝒶𝒷━
+ _ZZ
+ Z__
𝒵ₗ━━━
+ Z_Z

julia> projectZ!(copy(s), 1)[1] # = |000⟩ or |111⟩ (use projectZrand! to actually get a random result)
𝒟ℯ𝓈𝓉𝒶𝒷
+ XXX
+ _X_
+ __X
𝒮𝓉𝒶𝒷━
+ Z__
+ ZZ_
+ Z_Z
```

```julia-repl
julia> apply!(Register(copy(s)), sMRZ(1)) |> quantumstate # |000⟩ or |011⟩, depending on randomization
𝒟ℯ𝓈𝓉𝒶𝒷
+ XXX
+ _X_
+ __X
𝒮𝓉𝒶𝒷━
+ Z__
- ZZ_
- Z_Z
```

See also: [`Reset`](@ref), [`sMZ`](@ref)

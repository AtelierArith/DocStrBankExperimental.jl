量子ビットをZ基底で測定し、|0⟩状態にリセットします。

!!! 警告 "量子ビットをトレースアウトしません！"     下記に説明するように、量子ビットを測定すること（その後、既知の状態に設定すること）と「トレースアウト」することには違いがあります。ここでのリセットは「測定して既知の状態に設定する」ことを意味し、「トレースアウト」することではありません。

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

参照: [`Reset`](@ref), [`sMZ`](@ref)

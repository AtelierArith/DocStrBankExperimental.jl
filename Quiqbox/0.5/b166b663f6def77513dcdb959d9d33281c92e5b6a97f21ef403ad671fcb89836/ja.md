```
absorbNormFactor(b::BasisFunc{T, 3, 𝑙, GN, PT}) where {T, 𝑙, GN, PT} -> 
FloatingGTBasisFuncs{T, 3, 𝑙, GN, PT}

absorbNormFactor(b::BasisFuncs{T, 3, 𝑙, GN, PT}) where {T, 𝑙, GN, PT} -> 
Vector{<:FloatingGTBasisFuncs{T, 3, 𝑙, GN, PT}}
```

もし `hasNormFactor(`b`) == true` の場合、`b` 内の各ガウス型軌道の正規化因子を軌道の対応する収縮係数に吸収し、次に `b` の `.normalizeGTO` を `false` に設定します。そうでない場合、`b` が `BasisFunc` の場合は直接 `b` を返し、`BasisFuncs` の場合は `[b]` を返します。

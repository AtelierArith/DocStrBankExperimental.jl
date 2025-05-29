```
    SimplexLP(P::LP{T}; settings=Settings{T}(), min=true, Phase1=false)
    SimplexLP(c, A, b, d, u; settings=Settings{T}(), min=true, Phase1=false)
```

単純形法によってLPを解きます。`min=false`の場合、目的関数を最大化します。

出力     x               : 解,  N x 1 ベクトル     S               : Vector{Status}, (N+J)x1     status          : 1 一意; 0 不可解; 2 無限に多くの解; 3 無限大

詳細は [`Status`](@ref), [`LP`](@ref), [`Settings`](@ref), [`cDantzigLP`](@ref), [`maxImprvLP`](@ref) を参照してください。

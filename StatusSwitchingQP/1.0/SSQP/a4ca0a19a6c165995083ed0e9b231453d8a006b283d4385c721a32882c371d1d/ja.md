```
    solveQP(Q::QP{T}; settings, settingsLP) where T
    solveQP(V::Matrix{T}, q::Vector{T}, A, b, G, g, d, u; settings, settingsLP) where T
    solveQP(Q::QP{T}, S::Vector{Status}, x0; settings) where T
```

二次計画問題の場合：初期の実行可能点 (S, x0) が与えられた場合、SimplexLP から取得できます。

$$
    min   (1/2)z′Vz+q′z
    s.t.   Az=b ∈ R^{M}
           Gz≤g ∈ R^{J}
           d≤z≤u ∈ R^{N}
$$

出力

```
z               : 解,  N x 1 ベクトル
S               : Vector{Status}, (N+J)x1
status          : > 0 成功した場合 (=iter_count); = 0 非実行可能性が検出された場合; < 0 失敗 (-1 は数値エラー, -maxIter は収束しなかった場合)
```

参照してください [`QP`](@ref), [`SimplexLP`](@ref), [`Settings`](@ref), [`initQP`](@ref), [`initSSQP`](@ref)

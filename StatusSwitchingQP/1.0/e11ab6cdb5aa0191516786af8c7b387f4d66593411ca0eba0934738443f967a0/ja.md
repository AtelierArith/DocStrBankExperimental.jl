```
    QP(V::Matrix{T}; q, u, d, G, g, A, b) where T
    QP(P::QP{T}, q::Vector{T}, L::T=0.0) where T
    QP(P::QP{T}, mu::T, q::Vector{T}) where T
```

二次計画モデルを設定します：

$$
    min   (1/2)z′Vz+q′z
    s.t.   Az=b ∈ R^{M}
           Gz≤g ∈ R^{J}
           d≤z≤u ∈ R^{N}
$$

変数 z[i] は自由である可能性があり、例えば d[i]= -Inf および u[i]=+Inf です。M=0 の場合は等式はありません。デフォルト値：q = 0, u = +∞, d = 0, G = [], g = [], A = ones(1,N), b = [1] であり、次のようになります。

$$
    min   (1/2)z′Vz
    s.t.   1'z=1  ∈ R^{M}
           z≥0    ∈ R^{N}
$$

`QP(P::QP, q, L)`  :  目的関数の q'z 項を `-L * q` に置き換えます。`QP(P::QP, mu, c)` :  Az=b の最終行に c'z=mu を追加し、目的関数から q'z を削除します。

詳細は [`LP`](@ref), [`Settings`](@ref), [`solveQP`](@ref) を参照してください。

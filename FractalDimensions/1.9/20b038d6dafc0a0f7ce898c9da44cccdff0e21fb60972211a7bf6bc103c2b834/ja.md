```
estimate_r0_theiler(X::AbstractStateSpaceSet) → r0, ε0
```

データ `X` を計算する前にボックスの合理的なサイズを推定します [`boxed_correlationsum`](@ref) [Theiler1987](@cite) によって提案された。ボックスサイズ `r0` と `X` 内の最小点間距離 `ε0` を返します。

そのために、次のように次元を推定します。Grassberger と Procaccia [Grassberger1983](@cite) によるアルゴリズムを `√N` 点で実行します。ここで、`N` はデータポイントの総数です。次に、最適なボックスサイズ $r_0$ は次のように計算されます。

$$
r_0 = R (2/N)^{1/\nu}
$$

ここで、$R$ はカオスアトラクタのサイズであり、$\nu$ は推定された次元です。

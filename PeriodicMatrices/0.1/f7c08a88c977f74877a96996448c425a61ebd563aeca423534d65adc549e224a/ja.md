```
 phess(A::Array{Float64,3}; hind = 1, rev = true, withZ = true) -> (H, Z, ihess)
 phess1(A::Array{Float64,3}; hind = 1, rev = true, withZ = true) -> (H, Z, ihess)
```

行列の積 `A(p)*...*A(2)*A(1)` のヘッセンベルグ分解を計算します。`rev = true`（デフォルト）であれば、または `A(1)*A(2)*...*A(p)` の場合は `rev = false` で、積を評価することなく行います。行列 `A(1)`, `...`, `A(p)` は `n×n×p` 配列 `A` に含まれており、`i` 番目の行列 `A(i)` は `A[:,:,i]` に含まれています。結果として得られる `n×n×p` 配列 `H` と `Z` には、それぞれ行列 `H(1)`, `...`, `H(p)` と直交行列 `Z(1)`, `...`, `Z(p)` が含まれ、`rev = true` の場合は次のようになります。

```
       Z(2)' * A(1) * Z(1) = H(1),
       Z(3)' * A(2) * Z(2) = H(2),
              ...
       Z(1)' * A(p) * Z(p) = H(p),
```

`rev = false` の場合は次のようになります。

```
       Z(1)' * A(1) * Z(2) = H(1),
       Z(2)' * A(2) * Z(3) = H(2),
              ...
       Z(p)' * A(p) * Z(1) = H(p).
```

`hind = ihess` の場合、`1 ≤ ihess ≤ p`（デフォルトは `ihess = 1`）で、`H(i)`, `i = 1, ..., p` は周期的ヘッセンベルグ形式になり、`H(ihess)` は上ヘッセンベルグ形式で、`H(i)` は `i` $\neq$ `ihess` の場合上三角行列になります。`H(i)` と `Z(i)` はそれぞれ `H[:,:,i]` と `Z[:,:,i]` に含まれています。`withZ = false` の場合、実行された直交変換は蓄積されず、その場合 `Z = nothing` になります。

関数 `phess` は SLICOT サブルーチン `MB03VW` のラッパーに基づいています（[`PeriodicMatrices.SLICOTtools.mb03vw!`](@ref) を参照）。

関数 `phess1` は SLICOT サブルーチン `MB03VD` のラッパーに基づいています（[`PeriodicMatrices.SLICOTtools.mb03vd!`](@ref) を参照）および `MB03VY`（[`PeriodicMatrices.SLICOTtools.mb03vy!`](@ref) を参照）。

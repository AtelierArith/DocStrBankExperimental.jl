```
bestbasistreeall(X, method)
```

信号のセットの標準ベストバイスタリーを計算します。

# 引数

  * `X::AbstractArray{T} where T<:AbstractFloat`: サイズが `(n,L,k)` の1D信号または `(n,m,L,k)` の2D信号の分解された信号のセットで、ここで：

      * `n`: 信号の長さ（1D）または信号の垂直長（2D）。
      * `m`: 信号の水平長（2D）。
      * `L`: 分解レベルの数に1を加えたもの（標準ウェーブレット分解の場合）またはツリー内のノードの数（ACWTやSWTなどの冗長変換の場合）。
      * `k`: 信号の数。
  * `method::BB`: 標準ベストバイスタイムメソッド、例えば `BB()`。

# 戻り値

  * `::BitMatrix`: 各列がツリーに対応する `(nₜ,k)` 行列。

# 例

```julia
using Wavelets, WaveletsExt

X = generatesignals(:heavisine, 6) |> x -> duplicatesignals(x, 5, 2, true)
wt = wavelet(WT.db4)

Xw = wpdall(X, wt)
bestbasistreeall(Xw, BB())

Xw = swpdall(X, wt)
bestbasistree(Xw, BB(redundant=true))
```

**関連情報:** [`bestbasistree`](@ref)

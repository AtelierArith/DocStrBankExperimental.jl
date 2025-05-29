```
tree_costs(X, method)
```

バイナリツリー内の各ノードのコストを返し、最適な基底を見つけます。

# 引数

  * `X::AbstractArray{T} where T<:AbstractFloat`: 分解された信号のセットで、1D信号の場合はサイズが `(n,L,k)`、2D信号の場合は `(n,m,L,k)` です。ここで：

      * `n`: 信号の長さ（1D）または信号の縦の長さ（2D）。
      * `m`: 信号の横の長さ（2D）。
      * `L`: 分解レベルの数に1を加えたもの（標準ウェーブレット分解の場合）またはツリー内のノードの数（ACWTやSWTなどの冗長変換の場合）。
      * `k`: 信号の数。
  * `method::BestBasisType`: 最適基底のタイプ、つまり `BB()`、`JBB()` または `LSDB()`。

!!! note
    標準の最適基底（`BB()`）の場合、毎回1つの信号のみが処理されるため、入力 `X` は `(n,L)` または `(n,m,L)` の次元を持つ必要があります。


# 戻り値

  * `Vector{T}`: 各ノードのコストを含むベクター。

# 例

```julia
using Wavelets, WaveletsExt

X = generatesignals(:heavisine, 6) |> x -> duplicatesignals(x, 5, 2, true)
wt = wavelet(WT.db4)
Xw = wpdall(X, wt)

tree_costs(Xw, JBB())
tree_costs(Xw, LSDB())
```

**参照:** [`bestbasistree`](@ref), [`bestbasis_treeselection`](@ref)

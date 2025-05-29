```
local_outlier_factor_projection!(data::DataMatrix, full::DataMatrix, base::DataMatrix, base_full::DataMatrix; k=10, col="LOF_projection")
```

`data`内の各観測値に対してローカル外れ値因子（LOF）を計算し、`col`という名前の列として`data.obs`に追加します。

投影データを扱っている場合は`local_outlier_factor_projection!`を使用し、そうでない場合は[`local_outlier_factor!`](@ref)を使用してください。

パラメータ：

  * `data` - 各観測値に対してLOFを計算する`DataMatrix`。`data`と`base`が同じ座標系を使用するように、`base`に投影された`DataMatrix`であることが期待されます。
  * `full` - LOF計算で距離を計算するために使用される、`data`と同じ観測値を持つ`DataMatrix`。`full`と`base_full`が同じ座標系を使用するように、`base_full`に投影された`DataMatrix`であることが期待されます。
  * `base` - 基本の`DataMatrix`。
  * `base_full` - 基本の`DataMatrix`。
  * `k` - 使用する最近傍の数。注意：この関数は`k`の値が高いと非常に遅くなる可能性があります。

まず、`data`内の各観測値に対して、`base`内の`k`最近傍を見つけます。次に、`full`と`base_full`を使用して各隣接点までの距離を計算します。したがって、`full`は`data`に存在するのと同じ観測値を持ち、`base_full`は`base`と同じ観測値を持つ必要があります。

LOF値が1より小さいか、1に近い場合は、その観測値が内点であることを意味しますが、LOF値が1よりもはるかに大きい場合は、その観測値が外れ値であることを意味します。

`full=data`および`base_full=base`を指定することで、これはローカル外れ値因子の標準的な定義と一致します。しかし、次元削減された空間（例えば`svd`（PCA）や`umap`の後）で隣接点を見つけ、その後高次元空間（通常は正規化後）で距離を計算する方が有用な場合があります。この方法では、観測値が外れ値と見なされるのは、低次元空間への削減が観測値の近傍を適切に表現できなかった場合です。

!!! note
    インターフェースはまだ完全に決定されておらず、変更される可能性があります。


# 例

`base_reduced`に投影されたデータセット`reduced`内の各観測値に対してローカル外れ値因子（LOF）を計算します。

最近傍は`reduced`と`base_reduced`内の観測値の間で計算されますが、実際のLOF計算における距離は`normalized`と`base_normalized`内の同じ観測値の間で計算されます。

```julia
julia> base_reduced = svd(base_normalized; nsv=10)

julia> normalized = project(counts, base_normalized);

julia> reduced = project(normalized, base_reduced);

julia> local_outlier_factor!(reduced, normalized, base_reduced, base_normalized; k=10)
```

参照：[`local_outlier_factor_projection`](@ref)、[`local_outlier_factor_projection_table`](@ref)、[`local_outlier_factor!`](@ref)

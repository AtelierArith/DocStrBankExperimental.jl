```
local_outlier_factor!(data::DataMatrix, full::DataMatrix; k=10, col="LOF")
```

`data`内の各観測値に対してローカル外れ値因子（LOF）を計算し、`col`という名前の列として`data.obs`に追加します。

投影された`DataMatrices`を扱う場合は、代わりに[`local_outlier_factor_projection!`](@ref)を使用してください。

注意：この関数は、`k`の値が高いと非常に遅くなる可能性があります。

まず、`data`内の各観測値に対して`k`近傍を見つけます。次に、隣接点間の距離を考慮してローカル外れ値因子を計算しますが、今回は`full` DataMatrix内で行います。したがって、`full`は`data`に存在するのと同じ観測値を持っている必要があります。

LOFの値が1に近いかそれ以下であれば、その観測値は内点であることを意味しますが、LOFの値が1よりもはるかに大きい場合、その観測値は外れ値であることを意味します。

`full=data`を指定することで、これはローカル外れ値因子の標準的な定義と一致します。しかし、次元削減された空間（例えば、`svd`（PCA）や`umap`の後）で近傍を見つけ、その後高次元空間（通常は正規化後）で距離を計算する方が有用な場合があります。この方法では、低次元空間への削減が観測値の近傍を適切に表現していない場合、その観測値は外れ値と見なされます。

!!! note
    インターフェースはまだ完全に決定されておらず、変更される可能性があります。


# 例

`reduced`に基づいて近傍を見つけた後、実際のLOF計算には`full`内の距離を使用してローカル外れ値因子を計算します。

```julia
julia> reduced = svd(normalized; nsv=10)

julia> local_outlier_factor!(reduced, normalized; k=10)
```

関連情報：[`local_outlier_factor`](@ref)、[`local_outlier_factor_table`](@ref)、[`local_outlier_factor_projection!`](@ref)

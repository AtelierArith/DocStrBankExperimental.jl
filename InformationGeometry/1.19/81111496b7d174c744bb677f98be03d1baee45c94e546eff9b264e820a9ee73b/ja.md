```
DataSetExact(x::AbstractArray, y::AbstractArray, Σ_y::AbstractArray)
DataSetExact(x::AbstractArray, Σ_x::AbstractArray, y::AbstractArray, Σ_y::AbstractArray)
DataSetExact(xd::Distribution, yd::Distribution, dims::Tuple{Int,Int,Int}=(length(xd),1,1))
```

独立変数、すなわち $x$-変数に不確実性を持つデータコンテナです。さらに、観測データはそれぞれの空間 $\mathcal{X}^N$ と $\mathcal{Y}^N$ に対する二つの確率分布の形で保存されており、観測における非ガウス的な不確実性も許容されます。例えば、特定の観測に関連する不確実性は、コーシー分布、t-スチューデント分布、対数正規分布、または他の滑らかな分布に従うことがあります。

例:

```julia
using InformationGeometry, Distributions
X = product_distribution([Normal(0, 1), Cauchy(2, 0.5)])
Y = MvTDist(2, [3, 8.], [1 0.5; 0.5 3])
DataSetExact(X, Y, (2,1,1))
```

!!! note
    独立 $x$-変数における不確実性は `DataSetExact` にとってオプションであり、`x`-データを `InformationGeometry.Dirac` "分布" でラップすることによってゼロに設定できます。以下は、$x$-変数の不確実性がゼロであるデータセットをエンコードする数値的に同等な方法を示しています:

    ```julia
    using InformationGeometry, Distributions, LinearAlgebra
    DS1 = DataSetExact(InformationGeometry.Dirac([1,2]), MvNormal([5,6], Diagonal([0.1, 0.2].^2)))
    DS2 = DataSetExact([1,2], [5,6], [0.1, 0.2])
    DS3 = DataSet([1,2], [5,6], [0.1, 0.2])
    ```

    ここで `DS1 == DS2 == DS3` は `true` に評価されます。


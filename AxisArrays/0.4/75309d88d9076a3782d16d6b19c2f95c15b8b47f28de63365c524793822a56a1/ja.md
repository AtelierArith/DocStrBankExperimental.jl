```
collapse(::Val{N}, As::AxisArray...) -> AxisArray
collapse(::Val{N}, labels::Tuple, As::AxisArray...) -> AxisArray
collapse(::Val{N}, ::Type{NewArrayType}, As::AxisArray...) -> AxisArray
collapse(::Val{N}, ::Type{NewArrayType}, labels::Tuple, As::AxisArray...) -> AxisArray
```

`N` が等しい先頭軸を持つ `AxisArray` を単一の `AxisArray` に圧縮します。配列のいずれかにあるすべての追加軸は、型 `Axis{:collapsed, CategoricalVector{Tuple}}` の単一の追加軸に圧縮されます。

### 引数

  * `::Val{N}`: すべての入力配列間で共有する最大の共通次元。残りの軸は圧縮されます。すべての `N` 軸は、同じ次元で各入力配列に共通でなければなりません。値は `0` からすべての入力配列間の最小次元数まで許可されます。
  * `labels::Tuple`: (オプション) `As` の各配列に対するインデックスで、`:collapsed` 軸のインデックスタプルの先頭要素として使用されます。デフォルトは `1:length(As)` です。
  * `::Type{NewArrayType<:AbstractArray{_, N+1}}`: (オプション) 返される `AxisArray` のための希望する基礎配列型。
  * `As::AxisArray...`: 一緒に圧縮される `AxisArray`。

### 例

```
julia> price_data = AxisArray(rand(10), Axis{:time}(Date(2016,01,01):Day(1):Date(2016,01,10)))
1次元の AxisArray{Float64,1,...} で、軸は次の通りです:
    :time, 2016-01-01:1 day:2016-01-10
データは、10要素の Array{Float64,1}:
 0.885014
 0.418562
 0.609344
 0.72221
 0.43656
 0.840304
 0.455337
 0.65954
 0.393801
 0.260207

julia> size_data = AxisArray(rand(10,2), Axis{:time}(Date(2016,01,01):Day(1):Date(2016,01,10)), Axis{:measure}([:area, :volume]))
2次元の AxisArray{Float64,2,...} で、軸は次の通りです:
    :time, 2016-01-01:1 day:2016-01-10
    :measure, Symbol[:area, :volume]
データは、10×2の Array{Float64,2}:
 0.159434     0.456992
 0.344521     0.374623
 0.522077     0.313256
 0.994697     0.320953
 0.95104      0.900526
 0.921854     0.729311
 0.000922581  0.148822
 0.449128     0.761714
 0.650277     0.135061
 0.688773     0.513845

julia> collapsed = collapse(Val(1), (:price, :size), price_data, size_data)
2次元の AxisArray{Float64,2,...} で、軸は次の通りです:
    :time, 2016-01-01:1 day:2016-01-10
    :collapsed, Tuple{Symbol,Vararg{Symbol,N} where N}[(:price,), (:size, :area), (:size, :volume)]
データは、10×3の Array{Float64,2}:
 0.885014  0.159434     0.456992
 0.418562  0.344521     0.374623
 0.609344  0.522077     0.313256
 0.72221   0.994697     0.320953
 0.43656   0.95104      0.900526
 0.840304  0.921854     0.729311
 0.455337  0.000922581  0.148822
 0.65954   0.449128     0.761714
 0.393801  0.650277     0.135061
 0.260207  0.688773     0.513845

julia> collapsed[Axis{:collapsed}(:size)] == size_data
true
```

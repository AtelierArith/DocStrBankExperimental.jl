```julia
nanquantile!(A, q; dims)
```

`A`のすべての要素の`q`分位数（`q ∈ [0,1]`）を計算します。`NaN`を無視し、オプションで`dims`で指定された次元に対して計算します。

`StatsBase.quantile!`に似ていますが、`NaN`を無視し、`dims`キーワードをサポートしています。

`StatsBase.quantile!`と同様に、この関数は`A`を変更し、内容をソートまたは部分的にソートします（具体的には、`dims`で指定された次元に沿って、配列のサイズに応じて`quicksort!`または`quickselect!`を使用します）。`A`の内容を再配置したくない場合は、この関数を使用しないでください。

複数の`dims`に対する削減は公式にはサポートされていませんが、すべての次元が連続している限り、一般的に最適でない時間で動作します。

## 例

```julia
julia> using NaNStatistics

julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

 julia> nanquantile!(A, 0.5, dims=1)
 1×3 Matrix{Float64}:
  4.0  5.0  6.0

 julia> nanquantile!(A, 0.5, dims=2)
 3×1 Matrix{Float64}:
  2.0
  5.0
  8.0

 julia> nanquantile!(A, 0.5)
 5.0

 julia> A # 配列がソートされたことに注意してください
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9
```

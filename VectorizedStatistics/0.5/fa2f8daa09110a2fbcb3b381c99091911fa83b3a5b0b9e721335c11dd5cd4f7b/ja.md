```julia
vmedian!(A; dims)
```

`A`のすべての要素の中央値を計算します。オプションで、`dims`で指定された次元に対して計算できます。`Statistics.median!`と同様ですが、わずかにベクトル化されており、`dims`キーワードをサポートしています。

`Statistics.median!`と同様に、この関数は`A`を変更し、内容をソートまたは部分的にソートします（具体的には、`dims`で指定された次元に沿って、配列のサイズに応じて`quicksort!`または`quickselect!`を使用して中央値の周りで）。`A`の内容を再配置したくない場合は、この関数を使用しないでください。

複数の`dims`に対して縮小する場合、これらの次元は連続している必要があります（つまり、`dims=(2,3)`は許可されますが、`dims=(1,3)`は許可されません）。また、`:`以外の`dims`を指定すると、`view`が作成され、いくつかの非ゼロのパフォーマンスコストが発生します。

## 例

```julia
julia> using VectorizedStatistics

julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

 julia> vmedian!(A, dims=1)
 1×3 Matrix{Float64}:
  4.0  5.0  6.0

 julia> vmedian!(A, dims=2)
 3×1 Matrix{Float64}:
  2.0
  5.0
  8.0

 julia> vmedian!(A)
 5.0

 julia> A # 配列がソートされたことに注意してください
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9
```

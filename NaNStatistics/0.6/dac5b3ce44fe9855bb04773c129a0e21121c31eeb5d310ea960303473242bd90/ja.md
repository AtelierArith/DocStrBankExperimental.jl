```julia
nanmedian!(A; dims)
```

`A`のすべての要素の中央値を計算します。オプションで、`dims`で指定された次元に対して計算できます。`Statistics.median!`と同様ですが、`NaN`を無視し、`dims`キーワードをサポートします。

`Statistics.median!`と同様に、この関数は`A`を変更し、指定された次元に沿って内容をソートまたは部分的にソートします（具体的には、配列のサイズに応じて中央値の周りで`quicksort!`または`quickselect!`を使用します）。`A`の内容を再配置したくない場合は、この関数を使用しないでください。

複数の`dims`に対する削減は公式にはサポートされていませんが、削減される次元がすべて連続している限り、一般的に最適でない時間で動作します。

オプションで`dim`キーワードをサポートしており、これは`dims`と同様に動作しますが、削減された任意のシングルトン次元を削除します（これは他のいくつかの言語の慣例です）。

## 例

```julia
julia> using NaNStatistics

julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

 julia> nanmedian!(A, dims=1)
 1×3 Matrix{Float64}:
  4.0  5.0  6.0

 julia> nanmedian!(A, dims=2)
 3×1 Matrix{Float64}:
  2.0
  5.0
  8.0

 julia> nanmedian!(A)
 5.0

 julia> A # 配列がソートされたことに注意してください
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9
```

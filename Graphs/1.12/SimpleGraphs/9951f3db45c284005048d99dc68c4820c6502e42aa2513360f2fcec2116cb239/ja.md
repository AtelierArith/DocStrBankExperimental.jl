```
uniform_tree(n)
```

$$
n^{n-2}
$$

の木の中から一様にランダムに描かれたラベル付き木を生成します。アルファベット `1:n` に対する長さ `n-2` の一様な単語が生成され（プルーファー列）、その後デコードされます。`prufer_decode` 関数や [プルーファーコードに関するこのページ](https://en.wikipedia.org/wiki/Pr%C3%BCfer_sequence) も参照してください。

### オプション引数

  * `rng=nothing`: ランダム数生成器を設定します。

# 例

```jldoctest
julia> using Graphs

julia> uniform_tree(10)
{10, 9} undirected simple Int64 graph
```

```
flood_fill!(f, dest, src, idx, nbrhood_function=diamond_iterator((3,3,...)); fillvalue=true, isfilled = isequal(fillvalue))
```

`src` のすべての要素に対して、`dest` のエントリを `fillvalue` に設定します：

  * `f(src[i]) == true` を満たし、かつ
  * そのような要素によって開始点 `idx`（整数インデックスまたは `CartesianIndex`）に接続されている。

これは、`f` が開始値 `src[idx]` に対して `false` と評価される場合にエラーをスローします。接続の感覚は `nbrhood_function` によって定義され、[`ImageSegmentation.diamond_iterator`](@ref) と [`ImageSegmentation.box_iterator`](@ref) の2つの選択肢があります。

`dest` を省略することもできます。この場合、`src` のエントリが `fillvalue` に設定されます。これは、`fillvalue` が `src` の値と異なる場合にのみ推奨されます。そうでない場合、一部のボクセルが訪問済みとして誤って識別され、その隣接要素がさらなる検索から除外されるリスクがあります。また、`isfilled` を提供することもでき、これは `dest` の中で設定または訪問する必要がない任意の値に対して `true` を返す必要があります。1つの要件は `isfilled(fillvalue) == true` です。

# 例

```jldoctest; setup=:(using ImageSegmentation)
julia> a = repeat([1:4; 1:4], 1, 3)
8×3 Matrix{Int64}:
 1  1  1
 2  2  2
 3  3  3
 4  4  4
 1  1  1
 2  2  2
 3  3  3
 4  4  4

julia> flood_fill!(>=(3), a, CartesianIndex(3, 2); fillvalue = -1, isfilled = <(0))
8×3 Matrix{Int64}:
  1   1   1
  2   2   2
 -1  -1  -1
 -1  -1  -1
  1   1   1
  2   2   2
  3   3   3
  4   4   4
```

[`flood`](@ref) も参照してください。

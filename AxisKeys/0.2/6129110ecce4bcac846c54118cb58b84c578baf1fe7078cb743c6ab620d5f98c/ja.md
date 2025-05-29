```
wrapdims(A, :i, :j)
wrapdims(A, 1:10, ['a', 'b', 'c'])
wrapdims(A, i=1:10, j=['a', 'b', 'c'])
```

`NamedDimsArray`、`KeyedArray`、またはその両方のネストされたペアを構築するための便利な関数です。

`KeyedArray` コンストラクタによってスキップされるいくつかのサニティチェックを実行します：

  * キーの代わりに `nothing` を与えると、`axiskeys(A,d) == axes(A,d)` になります。
  * 長さが間違った `AbstractRange` が与えられた場合、これの終端を調整し、警告を出します。
  * `A::OffsetArray` とキーのベクトルがそうでない場合、それらをラップして `axes.(axiskeys(A_wrapped)) == axes(A)` になるようにします。

デフォルトでは、`KeyedArray{...,NamedDimsArray{...}}` の順序でラップされますが、`AxisKeys.nameouter() == true` を再定義することで変更できます。

# 例

```jldoctest
julia> wrapdims([1,10,100], pow=0:99)
┌ Warning: range 0:99 replaced by 0:2, to match size(A, 1) == 3
└ @ AxisKeys ~/.julia/dev/AxisKeys/src/wrap.jl:50
1-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   pow ∈ 3-element UnitRange{Int64}
And data, 3-element Vector{Int64}:
 (0)    1
 (1)   10
 (2)  100

julia> push!(ans, 1000)
1-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   pow ∈ 4-element UnitRange{Int64}
And data, 4-element Vector{Int64}:
 (0)     1
 (1)    10
 (2)   100
 (3)  1000
```

```
ByRow <: Function
```

`ByRow(f)` は、ベクトル内の各要素に関数 `f` を適用する関数を返します。

`ByRow(f)` には、2種類の引数を渡すことができます：

  * 同じ長さの1-based `AbstractVector`が1つ以上：この場合、返される値は、渡されたベクトルの要素に対して `f` を適用した結果のベクトルです。関数 `f` は、渡されたベクトルの各要素に対して正確に1回呼び出されます（対照的に、`map` は、ソースベクトルのいくつかのタイプ（例：`SparseVector`）に対してラップされた関数が純粋であると仮定し、複数の同じ値に対して関数 `f` を1回だけ呼び出すことがあります）。
  * 同じ長さの1-based 列を保持する `Tables.ColumnTable`：この場合、関数 `f` は、渡されたテーブルの各行のために作成された `NamedTuple` を受け取ります。

`ByRow(f)` の返り値は常にベクトルです。

`ByRow` は、少なくとも1つの引数が渡されることを期待しており、`Tables.ColumnTable` の場合は、テーブルに少なくとも1つの列があることが期待されます。テーブルに対する操作のいくつかの文脈（例えば `DataFrame`）では、ユーザーが `ByRow` に引数を渡さない（または空の `Tables.ColumnTable` を渡す）ことを望むかもしれません。この場合は、特定の親テーブルに対する `ByRow` 操作の処理ロジックを実装するコードによって別途処理される必要があります（その理由は、`ByRow` にそのような引数を渡すことが、ソーステーブルの行数を決定することを許可しないためです）。

# 例

```
julia> Tables.ByRow(x -> x^2)(1:3)
3-element Vector{Int64}:
 1
 4
 9

julia> Tables.ByRow((x, y) -> x*y)(1:3, 2:4)
3-element Vector{Int64}:
  2
  6
 12

julia> Tables.ByRow(x -> x.a)((a=1:2, b=3:4))
2-element Vector{Int64}:
 1
 2

 julia> Tables.ByRow(x -> (a=x.a*2, b=sin(x.b), c=x.c))((a=[1, 2, 3],
                                                         b=[1.2, 3.4, 5.6],
                                                         c=["a", "b", "c"]))
3-element Vector{NamedTuple{(:a, :b, :c), Tuple{Int64, Float64, String}}}:
 (a = 2, b = 0.9320390859672263, c = "a")
 (a = 4, b = -0.2555411020268312, c = "b")
 (a = 6, b = -0.6312666378723216, c = "c")

```

```
getall(obj, optic)
```

`optic`によって選択された`obj`のすべての部分を抽出します。値のフラットな`Tuple`を返すか、選択された部分に配列が含まれている場合は`AbstractVector`を返します。

`getall`の動作の詳細は実験的と見なされます。特に、正確な出力コンテナの型は将来的に変更される可能性があります。

[`setall`](@ref)も参照してください。

```jldoctest
julia> using Accessors

julia> obj = (a=1, b=(2, 3));

julia> getall(obj, @optic _.a)
(1,)

julia> getall(obj, @optic _ |> Elements() |> last)
(1, 3)
```

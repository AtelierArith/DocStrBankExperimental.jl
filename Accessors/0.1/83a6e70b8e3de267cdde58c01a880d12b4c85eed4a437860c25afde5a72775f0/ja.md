```
setall(obj, optic, values)
```

`optic`で選択された`obj`の一部を`values`で置き換えます。`values`コレクションは、`optic`で選択された要素と同じ数の要素を持つ必要があります。

`setall`の動作の詳細は実験的と見なされています。特に、`values`引数に対してサポートされるコンテナタイプは将来的に変更される可能性があります。

[`getall`](@ref)や[`set`](@ref)も参照してください。前者は`setall`の双対です：

```jldoctest
julia> using Accessors

julia> obj = (a=1, b=(2, 3));

julia> optic = @optic _ |> Elements() |> last;

julia> getall(obj, optic)
(1, 3)

julia> setall(obj, optic, (4, 5))
(a = 4, b = (2, 5))
```

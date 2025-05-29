```
AbstractAlgebra.set_assertion_level(s::Symbol, l::Int) -> Int
```

`s`が既知のアサーションスコープを表す場合、`s`の現在のアサーションレベルを`l`に設定します。

`s`の現在のアサーションレベルには、関数[`get_assertion_level`](@ref)を呼び出すことでアクセスできます。

`s`がまだアサーションスコープとして知られていない場合、関数は「Not a valid symbol」というエラーメッセージを示す`ErrorException`を発生させます。`s`をアサーションスコープのリストに追加するには、関数[`add_assertion_scope`](@ref)を呼び出します。

# 例

```jldoctest
julia> AbstractAlgebra.add_assertion_scope(:MyScope)

julia> AbstractAlgebra.set_assertion_level(:MyScope, 4)
4

julia> AbstractAlgebra.set_assertion_level(:MyScope, 0)
0
```

```
AbstractAlgebra.get_assertion_level(s::Symbol) -> Int
```

`s`が既知のアサーションスコープのシンボルを表す場合、`s`の現在のアサーションレベルを返します。

`s`の現在のアサーションレベルは、関数[`set_assertion_level`](@ref)を呼び出すことで変更できます。

`s`がまだアサーションスコープとして知られていない場合、関数は「Not a valid symbol」というエラーメッセージを示す`ErrorException`を発生させます。`s`をアサーションスコープのリストに追加するには、関数[`add_assertion_scope`](@ref)を呼び出すことができます。

# 例

```jldoctest
julia> AbstractAlgebra.add_assertion_scope(:MyScope)

julia> AbstractAlgebra.get_assertion_level(:MyScope)
0

julia> AbstractAlgebra.set_assertion_level(:MyScope, 1)
1

julia> AbstractAlgebra.get_assertion_level(:MyScope)
1

julia> AbstractAlgebra.set_assertion_level(:MyScope, 0)
0

julia> AbstractAlgebra.get_assertion_level(:MyScope)
0
```

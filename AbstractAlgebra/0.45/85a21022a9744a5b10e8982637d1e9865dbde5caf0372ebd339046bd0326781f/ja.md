```
AbstractAlgebra.get_verbosity_level(s::Symbol) -> Int
```

`s`が既知の冗長性スコープを表す場合、`s`の現在の冗長性レベルを返します。

`s`の現在の冗長性レベルは、関数[`set_verbosity_level`](@ref)を呼び出すことで変更できます。

`s`がまだ冗長性スコープとして知られていない場合、関数は「有効なシンボルではありません」というエラーメッセージを示す`ErrorException`を発生させます。`s`を冗長性スコープのリストに追加するには、関数[`add_verbosity_scope`](@ref)を呼び出します。

# 例

```jldoctest
julia> AbstractAlgebra.add_verbosity_scope(:MyScope)

julia> AbstractAlgebra.get_verbosity_level(:MyScope)
0

julia> AbstractAlgebra.set_verbosity_level(:MyScope, 4)
4

julia> AbstractAlgebra.get_verbosity_level(:MyScope)
4

julia> AbstractAlgebra.set_verbosity_level(:MyScope, 0)
0

julia> AbstractAlgebra.get_verbosity_level(:MyScope)
0
```

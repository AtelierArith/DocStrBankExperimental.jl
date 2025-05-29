```
AbstractAlgebra.set_verbosity_level(s::Symbol, l::Int) -> Int
```

`s`が既知の冗長性スコープを表す場合、`s`の現在の冗長性レベルを`l`に設定します。

`s`の現在の冗長性レベルには、関数[`get_verbosity_level`](@ref)を呼び出すことでアクセスできます。

`s`がまだ冗長性スコープとして知られていない場合、関数は「Not a valid symbol」というエラーメッセージを示す`ErrorException`を発生させます。`s`を冗長性スコープのリストに追加するには、関数[`add_verbosity_scope`](@ref)を呼び出します。

# 例

```jldoctest
julia> AbstractAlgebra.add_verbosity_scope(:MyScope)

julia> AbstractAlgebra.set_verbosity_level(:MyScope, 4)
4

julia> AbstractAlgebra.set_verbosity_level(:MyScope, 0)
0
```

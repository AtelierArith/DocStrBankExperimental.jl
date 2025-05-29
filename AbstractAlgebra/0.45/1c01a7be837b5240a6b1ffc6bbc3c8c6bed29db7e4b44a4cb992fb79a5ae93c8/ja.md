```
AbstractAlgebra.add_verbosity_scope(s::Symbol) -> Nothing
```

シンボル `s` を（グローバルな）冗長性スコープのリストに追加します。この関数はモジュール内で使用するためには、そのモジュールの `__init__` 関数内で呼び出す必要があります; その後、冗長性スコープはモジュール内のすべての関数で利用可能になります。

# 例

```jldoctest
julia> AbstractAlgebra.add_verbosity_scope(:MyScope)

```

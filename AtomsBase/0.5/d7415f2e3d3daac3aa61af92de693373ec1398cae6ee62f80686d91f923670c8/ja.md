```
AbstractSystem(system::AbstractSystem; kwargs...)
```

コンストラクタを更新します。1つ以上のプロパティが変更された新しいシステムを構築します。これらは`kwargs`として与えられます。`AbstractSystem`のサブタイプが返されます。デフォルトでは`FlexibleSystem`ですが、渡されたシステムのタイプによっては異なる場合があります。

サポートされている`kwargs`には`particles`、`atoms`、`cell_vectors`、および`periodicity`、さらにユーザー固有のカスタムプロパティが含まれます。

# 例

渡されたシステムのバウンディングボックスと原子を変更します。

```julia-repl
julia> AbstractSystem(system; cell_vectors= ..., atoms = ... )
```

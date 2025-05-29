```
Atom(atom::Atom; kwargs...)
```

コンストラクタを更新します。渡された `atom` オブジェクトに含まれるデータを修正することで新しい `Atom` を構築します。サポートされている `kwargs` には `species`、`mass`、およびユーザー固有のカスタムプロパティが含まれます。

# 例

原点に位置する標準的な水素原子を構築します

```julia-repl
julia> hydrogen = Atom(:H, zeros(3)u"Å")
```

そして、今度はその電荷と原子量を修正します

```julia-repl
julia> Atom(atom; mass=1.0u"u", charge=-1.0u"e_au")
```

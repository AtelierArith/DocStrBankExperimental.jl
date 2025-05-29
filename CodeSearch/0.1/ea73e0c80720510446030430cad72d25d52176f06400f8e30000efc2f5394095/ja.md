```
Pattern <: AbstractPattern
```

ワイルドカードを持つJulia式を表す構造体です。`Pattern`をマッチングする際、複数のマッチが互いに入れ子になる可能性があります。

この構造体のフィールドとコンストラクタは公開APIの一部ではありません。`Pattern`を作成するための公開APIについては、[`@j_str`](@ref)および[`pattern`](@ref)を参照してください。

`Pattern`オブジェクトを受け入れるメソッドは、`eachmatch`、`match`、`findall`、`findfirst`、`findlast`、`occursin`、および`count`に対して定義されています。

# 拡張ヘルプ

以下は実装の詳細です：

式は内部の`syntax_node`フィールドに通常の`SyntaxNode`として保存されます。その式のワイルドカードは、内部の`wildcard_symbol`フィールドに保存されたシンボルによって表されます。例えば、式`a + (b + *)`は`Pattern((call-i a + (call-i b + wildcard)), :wildcard)`として保存されるかもしれません。

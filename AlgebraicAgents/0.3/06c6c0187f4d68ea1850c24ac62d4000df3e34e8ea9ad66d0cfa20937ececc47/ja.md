```
typetree_mmd(T, TT; rem = false)
```

型 `T` の型階層の `Vector{String}` を返します。形式は [Mermaid](https://github.com/mermaid-js/mermaid) クラス図を作成するのに適しています。ルートケース（`T` が階層のトップである場合）では、`TT` は何も設定しないことができます（デフォルト引数）。

キーワード引数 `rem` を true に設定すると、型名からモジュールプレフィックスを削除します。これは Mermaid 図にとって便利です。なぜなら、Mermaid の classDiagram は現在、クラス名に "." 文字をサポートしていないからです。

# 例

```julia
# 次のコードは Mermaid ライブエディタに貼り付けることができます：
# https://mermaid.live/
print(join(typetree_mmd(Integer), ""))
```

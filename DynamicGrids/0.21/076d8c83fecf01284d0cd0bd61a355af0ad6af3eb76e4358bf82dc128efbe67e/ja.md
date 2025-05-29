```
TransformedOutput(f, init; tspan::AbstractRange, kw...)
```

グリッドのいくつかの関数 `f` の結果を格納する出力です。

# 引数

  * `f`: `AbstractArray` または `NamedTuple` の `AbstractArray` を受け入れる関数またはファンクタで、名前が `init` と一致します。`AbstractArray` は、追加されたパディングを取り除いた、初期グリッドと同じサイズのグリッドへのビューになります。
  * `init`: 初期化 `Array` または `Array` の `NamedTuple`

# キーワード

  * `tspan`: シミュレーションのための `AbstractRange` タイムスパン
  * `aux`: 任意の入力データの `NamedTuple`。型安定な方法で `Rule` からアクセスするには `get(data, Aux(:key), I...)` を使用します。
  * `mask`: 実行するセルと実行しないセルを定義するための `BitArray`。
  * `padval`: 隣接ルールを持つグリッドのためのパディング値。デフォルトは `zero(eltype(init))` です。

警告: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで 100% 信頼できるわけではありません。問題が発生した場合は、github の問題を報告してください。

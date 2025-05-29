```
ResultOutput <: Output

ResultOutput(init; tspan::AbstractRange, kw...)
```

最終結果のみを保存し、中間フレームは保存しないシンプルな出力です。

# 引数

  * `init`: 初期化 `Array` または `NamedTuple` の `Array`

# キーワード（[`Extent`](@ref) に渡される）

  * `init`: グリッド/s の初期化 `Array`/`NamedTuple`。
  * `mask`: 実行するセルと実行しないセルを定義するための `BitArray`。
  * `aux`: 任意の入力データの `NamedTuple`。型安定な方法で `Rule` からアクセスするには `aux(data, Aux(:key))` を使用します。
  * `padval`: 隣接ルールを持つグリッドのパディング値。デフォルトは `zero(eltype(init))` です。
  * `tspan`: 時間範囲。決して型安定ではなく、`modifyrule` メソッド内でのみアクセスします。

`Extent` オブジェクトも `extent` キーワードに渡すことができ、他のキーワードは無視されます。

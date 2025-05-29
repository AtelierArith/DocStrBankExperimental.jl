```
ArrayOutput <: Output

ArrayOutput(init; tspan::AbstractRange, [aux, mask, padval])
```

シミュレーションの各ステップを配列のベクトルに格納するシンプルな出力です。

# 引数

  * `init`: 初期化 `AbstractArrayArray` または `AbstractArrayArray` の `NamedTuple`。

# キーワード（[`Extent`](@ref) に渡される）

  * `init`: グリッドのための初期化 `Array`/`NamedTuple`。
  * `mask`: 実行するセルと実行しないセルを定義するための `BitArray`。
  * `aux`: 任意の入力データの `NamedTuple`。型安定な方法で `Rule` からアクセスするには `aux(data, Aux(:key))` を使用します。
  * `padval`: 隣接ルールを持つグリッドのためのパディング値。デフォルトは `zero(eltype(init))` です。
  * `tspan`: 時間範囲。型安定ではなく、`modifyrule` メソッド内でのみアクセスしてください。

`Extent` オブジェクトも `extent` キーワードに渡すことができ、他のキーワードは無視されます。

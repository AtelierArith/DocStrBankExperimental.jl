```
REPLOutput <: GraphicOutput

REPLOutput(init; tspan, kw...)
```

REPLに直接表示される出力です。シミュレーションフレームを保存するか破棄することができます。

# 引数:

  * `init`: 初期化 `AbstractArrayArray` または `AbstractArrayArray` の `NamedTuple`。

# キーワード

  * `color`: Crayons.jl からの色
  * `cutoff`: 完全なセルまたは空のセルを表示するための `Real` カットオフポイント。デフォルトは `0.5`
  * `style`: `CharStyle` `Block()` または `Braile()` 印刷。`Braile` は `Block` の1/4の画面スペースを使用します。

## [`Extent`](@ref) キーワード:

  * `init`: グリッドの初期化 `Array`/`NamedTuple`。
  * `mask`: 実行するセルと実行しないセルを定義するための `BitArray`。
  * `aux`: 任意の入力データの `NamedTuple`。`Rule` から型安定な方法でアクセスするには `aux(data, Aux(:key))` を使用します。
  * `padval`: 隣接ルールを持つグリッドのパディング値。デフォルトは `zero(eltype(init))` です。
  * `tspan`: 時間範囲。決して型安定ではなく、`modifyrule` メソッド内でのみアクセスします。

`Extent` オブジェクトは `extent` キーワードにも渡すことができ、他のキーワードは無視されます。

## [`GraphicConfig`](@ref) キーワード:

  * `fps::Real`: 秒あたりのフレーム数。
  * `store::Bool`: `ArrayOutput` のようにフレームを保存するか、視覚化後に破棄するか。非常に長いシミュレーション実行は、`store=true` の場合に利用可能なメモリを埋める可能性があります。

`GraphicConfig` オブジェクトは `graphicconfig` キーワードにも渡すことができ、他のキーワードは無視されます。

`GraphicConfig` オブジェクトは `graphicconfig` キーワードにも渡すことができ、他のキーワードは無視されます。

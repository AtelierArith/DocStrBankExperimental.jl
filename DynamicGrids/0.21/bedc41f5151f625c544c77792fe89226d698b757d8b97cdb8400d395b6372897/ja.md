```
GifOutput <: ImageOutput

GifOutput(init; filename, tspan, kw...)
```

出力はシミュレーションを画像として保存し、完了時にGifファイルを保存します。

# 引数:

  * `init`: 初期化 `AbstractArrayArray` または `AbstractArrayArray` の `NamedTuple`。

# キーワード

Gifを保存する:

  * `filename`: Gifファイルを保存するためのファイルパス。

## [`Extent`](@ref) キーワード:

  * `init`: グリッドのための初期化 `Array`/`NamedTuple`。
  * `mask`: 実行するセルと実行しないセルを定義するための `BitArray`。
  * `aux`: 任意の入力データの `NamedTuple`。`aux(data, Aux(:key))` を使用して、型安定な方法で `Rule` からアクセスします。
  * `padval`: 隣接ルールを持つグリッドのためのパディング値。デフォルトは `zero(eltype(init))` です。
  * `tspan`: 時間範囲。型安定ではなく、`modifyrule` メソッド内でのみアクセスします。

`Extent` オブジェクトも `extent` キーワードに渡すことができ、他のキーワードは無視されます。

## [`GraphicConfig`](@ref) キーワード:

  * `fps::Real`: 秒あたりのフレーム数。
  * `store::Bool`: `ArrayOutput` のようにフレームを保存するか、視覚化後に破棄するか。非常に長いシミュレーションは、`store=true` の場合に利用可能なメモリを消費する可能性があります。

`GraphicConfig` オブジェクトも `graphicconfig` キーワードに渡すことができ、他のキーワードは無視されます。

## [`ImageConfig`](@ref) キーワード:

  * `minval`: RGBピクセルへの変換のために正規化するグリッド内の最小値。`layout` 配列に一致する複数のグリッド用の `Vector/Matrix`。注意: デフォルトは `0` で、シミュレーションのために自動的に更新されません。
  * `maxval`: RGBピクセルへの変換のために正規化するグリッド内の最大値。`layout` 配列に一致する複数のグリッド用の `Vector/Matrix`。注意: デフォルトは `1` で、シミュレーションのために自動的に更新されません。
  * `font`: 検索するフォントの `String` 名。デフォルトが推測されます。
  * `text`: テキストなしの場合は `TextConfig()` または `nothing`。デフォルトは `TextConfig(; font=font)` です。
  * `scheme`: ColorSchemes.jl のカラースキーム、[`ObjectScheme`](@ref) または `Base.get(obj, val)` を定義し、`Color` または `ARGB32(val)` を使用して `Color` に変換できる値を返すオブジェクト。
  * `zerocolor`: 値がゼロのときに使用する `Col`、または無視するための `nothing`。
  * `maskcolor`: セルがマスクされているときに使用する `Color`、または無視するための `nothing`。
  * `renderer`: [`Renderer`](@ref) のような [`Image`](@ref) または [`Layout`](@ref)。自動的に検出され、利用可能な場合は `scheme`、`zerocolor`、`maskcolor` キーワードを使用します。複数のグリッド用の `Vector/Matrix` で、`layout` 配列に一致することができます。

`ImageConfig` オブジェクトも `imageconfig` キーワードに渡すことができ、他のキーワードは無視されます。

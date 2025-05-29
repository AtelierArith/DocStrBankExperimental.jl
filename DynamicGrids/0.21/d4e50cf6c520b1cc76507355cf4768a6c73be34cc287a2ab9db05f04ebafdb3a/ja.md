```
GraphicOutput <: Output
```

シミュレーションフレームを表示するための[`Output`](@ref)の抽象スーパタイプです。

すべての`GraphicOutputs`は[`GraphicConfig`](@ref)オブジェクトを持ち、[`showframe`](@ref)メソッドを定義する必要があります。

例として[`REPLOutput`](@ref)を参照してください。

# すべての`GraphicOutput`のユーザー引数:

  * `init`: 初期化`AbstractArray`または`NamedTuple`の`AbstractArray`

# すべての`GraphicOutput`の最小ユーザーキーワード:

## [`Extent`](@ref)キーワード:

  * `init`: グリッドのための初期化`Array`/`NamedTuple`。
  * `mask`: 実行するセルと実行しないセルを定義するための`BitArray`。
  * `aux`: 任意の入力データのNamedTuple。`aux(data, Aux(:key))`を使用して、型安定な方法で`Rule`からアクセスします。
  * `padval`: 隣接ルールを持つグリッドのためのパディング値。デフォルトは`zero(eltype(init))`です。
  * `tspan`: 時間範囲。型安定ではなく、`modifyrule`メソッド内でのみアクセスしてください。

`Extent`オブジェクトは`extent`キーワードに渡すこともでき、他のキーワードは無視されます。

## [`GraphicConfig`](@ref)キーワード:

  * `fps::Real`: 秒あたりのフレーム数。
  * `store::Bool`: `ArrayOutput`のようにフレームを保存するか、視覚化後に破棄するか。非常に長いシミュレーションは、`store=true`のときに利用可能なメモリを埋める可能性があります。

`GraphicConfig`オブジェクトは`graphicconfig`キーワードに渡すこともでき、他のキーワードは無視されます。

## `GraphicOutput`を拡張するオブジェクトのコンストラクタ用内部キーワード:

デフォルトのコンストラクタはこれらのオブジェクトを生成し、継承するオブジェクトのコンストラクタに渡します。これには以下のキーワードを受け入れる必要があります:

  * `frames`: シミュレーションフレームの`Vector`（`NamedTuple`または`Array`）。
  * `running`: `Bool`。
  * `extent`: [`Extent`](@ref)オブジェクト。
  * `graphicconfig`: [`GraphicConfig`](@ref)オブジェクト。

ユーザーは必要に応じてこれらのオブジェクト全体を渡すこともできます。

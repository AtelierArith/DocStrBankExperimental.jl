```
ImageOutput <: GraphicOutput
```

シミュレーションフレームをRGB画像として表示するGraphic出力の抽象スーパークラスです。

`ImageOutput`は[`Extent`](@ref)、[`GraphicConfig`](@ref)、および[`ImageConfig`](@ref)コンポーネントを持ち、[`showimage`](@ref)メソッドを定義する必要があります。

例として[`GifOutput`](@ref)を参照してください。

コードの大部分は共有と再利用を可能にするためにここに維持されていますが、ほとんどの`ImageOutput`は、グラフィックスライブラリへの重い依存関係を避けるためにDynamicGrids.jlには提供されていません。実装については[DynamicGridsGtk.jl](https://github.com/cesaraustralia/DynamicGridsGtk.jl)および[DynamicGridsInteract.jl](https://github.com/cesaraustralia/DynamicGridsInteract.jl)を参照してください。

# すべての`GraphicOutput`のユーザー引数:

  * `init`: 初期化`AbstractArray`または`NamedTuple`の`AbstractArray`

# すべての`ImageOutput`の最小ユーザーキーワード:

## [`Extent`](@ref)キーワード:

  * `init`: グリッドの初期化`Array`/`NamedTuple`。
  * `mask`: 実行するセルと実行しないセルを定義するための`BitArray`。
  * `aux`: 任意の入力データのNamedTuple。`aux(data, Aux(:key))`を使用して、型安定な方法で`Rule`からアクセスします。
  * `padval`: 隣接ルールを持つグリッドのパディング値。デフォルトは`zero(eltype(init))`です。
  * `tspan`: 時間範囲。型安定ではなく、`modifyrule`メソッド内でのみアクセスしてください。

`Extent`オブジェクトは`extent`キーワードに渡すこともでき、他のキーワードは無視されます。

## [`GraphicConfig`](@ref)キーワード:

  * `fps::Real`: 秒あたりのフレーム数。
  * `store::Bool`: `ArrayOutput`のようにフレームを保存するか、視覚化後に破棄するか。非常に長いシミュレーションは、`store=true`のときに利用可能なメモリを埋める可能性があります。

`GraphicConfig`オブジェクトは`graphicconfig`キーワードに渡すこともでき、他のキーワードは無視されます。

## [`ImageConfig`](@ref)キーワード:

  * `minval`: RGBピクセルへの変換のために正規化するグリッド内の最小値。`layout`配列に一致する複数のグリッド用の`Vector/Matrix`。注意: デフォルトは`0`で、シミュレーションのために自動的に更新されません。
  * `maxval`: RGBピクセルへの変換のために正規化するグリッド内の最大値。`layout`配列に一致する複数のグリッド用の`Vector/Matrix`。注意: デフォルトは`1`で、シミュレーションのために自動的に更新されません。
  * `font`: 検索するフォントの`String`名。デフォルトが推測されます。
  * `text`: テキストなしの場合は`TextConfig()`または`nothing`。デフォルトは`TextConfig(; font=font)`です。
  * `scheme`: ColorSchemes.jlのカラースキーム、[`ObjectScheme`](@ref)または`Base.get(obj, val)`を定義し、`Color`または`Color`に変換可能な値を返すオブジェクト。
  * `zerocolor`: 値がゼロのときに使用する`Col`、または無視するための`nothing`。
  * `maskcolor`: セルがマスクされているときに使用する`Color`、または無視するための`nothing`。
  * `renderer`: [`Renderer`](@ref)のような[`Image`](@ref)または[`Layout`](@ref)。自動的に検出され、利用可能な場合は`scheme`、`zerocolor`、および`maskcolor`キーワードを使用します。複数のグリッド用の`Vector/Matrix`で、`layout`配列に一致することができます。

`ImageConfig`オブジェクトは`imageconfig`キーワードに渡すこともでき、他のキーワードは無視されます。

## `GraphicOutput`を拡張するオブジェクトのコンストラクタ用の内部キーワード:

デフォルトのコンストラクタはこれらのオブジェクトを生成し、継承するオブジェクトのコンストラクタに渡します。これには以下のキーワードを受け入れる必要があります:

  * `frames`: シミュレーションフレームの`Vector`（`NamedTuple`または`Array`）。
  * `running`: `Bool`。
  * `extent`: [`Extent`](@ref)オブジェクト。
  * `graphicconfig`: [`GraphicConfig`](@ref)オブジェクト。
  * `imageconfig`: [`ImageConfig`](@ref)オブジェクト。

ユーザーは必要に応じてこれらのオブジェクト全体を渡すこともできます。

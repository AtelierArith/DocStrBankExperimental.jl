```
savegif(filename::String, o::Output; kw...)
```

出力配列をgifに書き込みます。

# 引数

  * `filename`: gifファイルを保存するためのファイルパス。
  * `output`: [`Output`](@ref)オブジェクト。gifを作成するには、出力がフレームを保存し、`store=true`で実行され、`@assert DynamicGrids.istored(o)`が通過する必要があります。

# キーワード

[`ImageConfig`](@ref)キーワード:

  * `minval`: RGBピクセルへの変換のために正規化するグリッド内の最小値。`layout`配列に一致する複数のグリッド用の`Vector/Matrix`。注意: デフォルトは`0`で、シミュレーションのために自動的に更新されません。
  * `maxval`: RGBピクセルへの変換のために正規化するグリッド内の最大値。`layout`配列に一致する複数のグリッド用の`Vector/Matrix`。注意: デフォルトは`1`で、シミュレーションのために自動的に更新されません。
  * `font`: 検索するフォントの`String`名。デフォルトが推測されます。
  * `text`: テキストなしの場合は`TextConfig()`または`nothing`。デフォルトは`TextConfig(; font=font)`です。
  * `scheme`: ColorSchemes.jlのカラースキーム、[`ObjectScheme`](@ref)または`Base.get(obj, val)`を定義し、`Color`または`ARGB32(val)`を使用して`Color`に変換できる値を返すオブジェクト。
  * `zerocolor`: 値がゼロのときに使用する`Col`、または無視するための`nothing`。
  * `maskcolor`: セルがマスクされているときに使用する`Color`、または無視するための`nothing`。
  * `renderer`: [`Renderer`](@ref)のような[`Image`](@ref)または[`Layout`](@ref)。自動的に検出され、利用可能な場合は`scheme`、`zerocolor`、`maskcolor`キーワードを使用します。`layout`配列に一致する複数のグリッド用の`Vector/Matrix`である可能性があります。

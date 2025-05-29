```
@newmodelgc modelname parent paramstype [sitemodel = true, use_struct_param = false]
```

これはEoSモデルを使用するために必要なすべての情報を含むデータ型です。また、正しい関数が呼び出されることを保証するための識別子としても機能します。

このモデルを使用するサイトを使用するかどうかを示すオプションの4番目の`Bool`引数を渡すことができます。デフォルトは`true`です。

また、2次のGroupParam（`StructGroupParam`）が使用されるかどうかを示す別のオプションの5番目の`Bool`引数を渡すこともできます。デフォルトは`false`です。

= フィールド = 構造体は以下のフィールドで構成されています：

  * components: コンポーネントの文字列リスト
  * groups: a [`GroupParam`](@ref)
  * sites: a [`SiteParam`](@ref) (オプション)
  * params: モデル内のすべてのパラメータを含む構造体のparamstype
  * idealmodel: 使用する理想モデルを決定するIdealModel構造体
  * assoc_options: 連携ソルバーのオプションを含む構造体。see [`AssocOptions`](@ref)
  * references: このEoSの参照

チュートリアルを参照するか、実装をブラウズして、これがどのように使用されるかを確認してください。

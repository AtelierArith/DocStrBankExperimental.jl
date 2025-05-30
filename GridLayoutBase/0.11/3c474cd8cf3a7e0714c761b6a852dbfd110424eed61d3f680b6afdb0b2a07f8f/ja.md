```
struct LayoutObservables{G}
```

`T`は含まれている`GridContent`の同じ型パラメータであり、`G`は`LayoutObservables`の後にのみ定義される`GridLayout`です。

MakieLayoutレイアウトシステムとインターフェースするために必要な`Observable`のコレクションとオプションの`GridContent`です。

  * `suggestedbbox::Observable{Rect2f}`: 要素が自分自身を配置すべきバウンディングボックス。要素の`width`および`height`属性に応じて、これは必ずしもcomputedbboxと等しいわけではありません。
  * `protrusions::Observable{RectSides{Float32}}`: メイン要素から`GridLayout`の隙間に「突き出ている」コンテンツのサイズ。
  * `reporteddimensions::Observable{Dimensions}`: オブジェクトが含まれている`GridLayout`に伝える寸法（内寸および外寸）。
  * `autosize::Observable{NTuple{2, Optional{Float32}}}`: 要素が親の`GridLayout`に報告する幅と高さ。要素が親に自分のサイズに調整させたくない場合、autosizeは報告されたサイズを`nothing`に設定することで隠すことができます。
  * `computedbbox::Observable{Rect2f}`: 要素がsuggestedbboxを受け取った後に自分自身のために計算するバウンディングボックス。
  * `gridcontent::Optional{GridContent{G}}`: 要素が現在`GridLayout`に配置されている場合の`GridContent`の参照。これを使用して親レイアウトを取得したり、要素をそこから削除したり、位置を変更したり、異なるレイアウトに割り当てたりすることができます。

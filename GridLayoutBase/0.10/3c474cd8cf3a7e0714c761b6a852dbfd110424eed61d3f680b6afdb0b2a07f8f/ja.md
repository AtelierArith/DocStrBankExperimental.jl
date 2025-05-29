```
struct LayoutObservables{G}
```

`T` は含まれている `GridContent` の同じ型パラメータであり、`G` は `LayoutObservables` の後にのみ定義される `GridLayout` です。

MakieLayout レイアウトシステムとインターフェースするために必要な `Observable` のコレクションとオプションの `GridContent` です。

  * `suggestedbbox::Observable{Rect2f}`: 要素が自分自身を配置すべきバウンディングボックスです。要素の `width` と `height` 属性に応じて、これは必ずしも computedbbox と等しいわけではありません。
  * `protrusions::Observable{RectSides{Float32}}`: メイン要素から `GridLayout` の隙間に「突き出ている」コンテンツのサイズです。
  * `reporteddimensions::Observable{Dimensions}`: オブジェクトが含まれている `GridLayout` に伝える寸法（内寸と外寸）です。
  * `autosize::Observable{NTuple{2, Optional{Float32}}}`: 要素が親の `GridLayout` に報告する幅と高さです。要素が親に自分のサイズに合わせて調整させたくない場合、autosize を `nothing` に設定することで報告されたサイズを隠すことができます。
  * `computedbbox::Observable{Rect2f}`: 要素が suggestedbbox を受け取った後に自分自身のために計算するバウンディングボックスです。
  * `gridcontent::Optional{GridContent{G}}`: 要素が現在 `GridLayout` に配置されている場合の `GridContent` の参照です。これを使用して親レイアウトを取得したり、要素をそこから削除したり、位置を変更したり、別のレイアウトに割り当てたりすることができます。

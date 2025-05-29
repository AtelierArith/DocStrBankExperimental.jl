```
mutable struct LayoutObservables{T, G}
```

`T` は含まれている `GridContent` の同じ型パラメータであり、`G` は `LayoutObservables` の後にのみ定義される `GridLayout` です。

MakieLayout レイアウトシステムとインターフェースするために必要な `Observable` のコレクションとオプションの `GridContent` です。

  * `suggestedbbox::Observable{FRect2D}`: 要素が自分自身を配置すべきバウンディングボックスです。要素の `width` と `height` 属性に応じて、これは必ずしも computedbbox と等しいわけではありません。
  * `protrusions::Observable{RectSides{Float32}}`: メイン要素から `GridLayout` の隙間に「突き出ている」コンテンツのサイズです。
  * `reportedsize::Observable{NTuple{2, Optional{Float32}}}`: 要素が可能であれば自分自身のために計算する幅と高さ（そうでなければ `nothing`）。
  * `autosize::Observable{NTuple{2, Optional{Float32}}}`: 要素が親の `GridLayout` に報告する幅と高さです。要素が親に自分のサイズに調整させたくない場合、autosize を `nothing` に設定することで reportedsize を隠すことができます。
  * `computedbbox::Observable{FRect2D}`: 要素が suggestedbbox を受け取った後に自分自身のために計算するバウンディングボックスです。
  * `gridcontent::Optional{GridContent{G, T}}`: 要素が現在 `GridLayout` に配置されている場合の `GridContent` の参照です。これを使用して親レイアウトを取得したり、要素をそこから削除したり、位置を変更したり、異なるレイアウトに割り当てたりすることができます。

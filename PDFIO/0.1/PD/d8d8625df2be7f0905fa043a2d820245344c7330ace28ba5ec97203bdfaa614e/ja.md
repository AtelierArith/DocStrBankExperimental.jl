```
    PDPageObject
```

PDFページに関連付けられたコンテンツストリームには、レンダリング可能なオブジェクトが含まれています。これらのオブジェクトは`PDPageObject`によって表されます。これらのオブジェクトは、オペランドの前に付けられた後置記法の演算子を含むことができます。例えば：

```
(Draw this text) Tj
```

上記のように、文字列オブジェクトは[`CosString`](@ref)であり、オペランド`Tj`、つまりテキストを描画するためのパラメータです。これらのオブジェクトのクラスは[`PDPageElement`](@ref)によって表されます。

しかし、特定のオブジェクトは、グループ化情報やグループ化情報の開始および終了マーカーのみを提供します。例えば、テキストオブジェクト：

```
BT
    /F1 11 Tf  %selectfont
    (Draw this text) Tj
ET
```

この種のオブジェクトは[`PDPageObjectGroup`](@ref)によって表されます。この場合、[`PDPageObjectGroup`](@ref)は4つの[`PDPageElement`](@ref)を含みます。具体的には、演算子`BT`、`Tf`、`Tj`、`ET`として表されます。

`PDPageElement`と[`PDPageObjectGroup`](@ref)は、合成によって拡張できます。したがって、さらに専門的なオブジェクトも見ることができます。

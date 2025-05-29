```
bremsstrahlung(::Type{<:NeXLBremsstrahlung}, e::AbstractFloat, e0::AbstractFloat, elm::Element)
```

エネルギー `e` におけるブレムストラールング（連続体）を、元素 `elm` における入射電子のエネルギー `e0` に対して計算します。

サポートされているモデルには、Kramers1923、Lifshin1974、Reed1975、Smith1975、Small1987、Trincavelli1997、Castellano2004a、Castellano2004b が含まれます。

モデルを評価したところ、Castellano2004a と Trincavelli1997 は Riveros1993 マトリックス補正アルゴリズムおよび AP33Tabulation ウィンドウとよく機能することがわかりました。Smith1975 は CitZAF マトリックス補正モデルと驚くほどよく機能します。他の古いモデルは Si(Li) データに基づいているため、低エネルギーではあまりうまく機能しない傾向があります。これに驚く人はいないでしょう。なぜなら、これらのモデルはしばしば Be ウィンドウ検出器からのデータに基づいていたからです。Castellano2004a と Trincavelli1997 は Riveros1993 マトリックス補正モデルを中心に設計されており、CitZAF を使用するとあまり良いパフォーマンスを発揮しません。

私の現在の推奨は、Castellano2004a または Riveros1993 です。

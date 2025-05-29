```
label_flatzones(img; [dims])
label_flatzones(img; se)
```

画像 'img' のフラットゾーンを見つけます。フラットゾーンは、同じ値を持つ接続された（seに関して）ボクセルとして定義されます。

`dims` キーワードは、ボックス形状の構造要素 [`strel_box(img; dims)`](@ref strel_box) を構築することによって処理する次元を指定するために使用されます。一般的な構造要素の場合、半サイズは各次元に沿って `0` または `1` であることが期待されます。

出力 `labeled image` は整数配列です。

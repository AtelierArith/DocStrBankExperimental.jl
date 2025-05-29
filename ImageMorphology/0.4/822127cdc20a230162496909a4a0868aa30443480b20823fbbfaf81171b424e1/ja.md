```
regional_minima(img; [dims])
regional_minima(img; se)
```

画像のすべての局所最小値を決定します。

グレースケール画像 `img` において、局所最小値は、同じ値を持ち、その値がセットの直接的な隣接ピクセルの値よりも低い接続されたピクセルの集合として定義されます。

`dims` キーワードは、ボックス形状の構造要素 [`strel_box(img; dims)`](@ref strel_box) を構築することによって処理する次元を指定するために使用されます。一般的な構造要素の場合、半サイズは各次元に沿って `0` または `1` であることが期待されます。

# 注意 この実装は、maxtree が事前に計算されていない場合、maxtree の local_minima アプローチよりも高速です。

# 参照

この関数のインプレースバージョンは `regional_minima!` です。

# 参考文献

  * [1] L. Vincent, “Morphological grayscale reconstruction in image analysis: applications   and efficient algorithms,” IEEE Trans. on Image Process., vol. 2, no. 2, pp. 176–201, Apr.   1993, doi: 10.1109/83.217222.
  * [2] P. Soille, Morphological Image Analysis. Berlin, Heidelberg: Springer Berlin   Heidelberg, 2004. doi: 10.1007/978-3-662-05088-0.

```
matrix_to_graph(matrix; diagonal = true, attribute="weight")
matrix_to_graph(array_3d; diagonal = true, attributes = ["weight$i" for i in 1:size(array_3d)[3]])
```

行列から `DataGraph` オブジェクトを構築し、行列データを `attribute` という名前のノード属性として保存します。`diagonal = false` の場合、グラフはメッシュ構造を持ち、各行列のエントリはノードとして表され、各ノードは隣接する行列のエントリ/ノードに接続されます。`diagonal = true` の場合、行列のエントリはそれに対角にあるノードにも接続されます（すなわち、エントリ (i,j) は (i-1, j-1)、(i + 1, j -1) などに接続されます）。

3D 行列が関数に渡されると、最初の2次元を行列として扱い、3次元のデータを異なる重みとして保存します（すなわち、サイズ dim1、dim2、dim3 の配列の場合、エントリ (i,j) は dim3 の重みを持ちます）。`attribute_list` はユーザーによって定義され、3次元の各重みに名前を付けることができます。

Function for reading gmsh's mesh format files http://gmsh.info/doc/texinfo/gmsh.html#MSH-file-format

```
Input:
    - mshFilename: 読み込む .msh ファイルの名前

Output:
    - nodesMat: 4 列の行列: [x y z physicalTag]
    - conecMat: 5 列の行列: [ n1 n2 n3 n4 physicalTag ] ノードが 4 未満の要素の場合、0 がノードインデックスとして使用されます。
    - physicalNames: 物理名の文字列を含むセル。

Assumptions:
    - 物理名は文字列として保存されます
    - エンティティごとに最大 1 つの物理タグ
    - 要素ごとの最大ノード数: 4 (線形四面体)
```

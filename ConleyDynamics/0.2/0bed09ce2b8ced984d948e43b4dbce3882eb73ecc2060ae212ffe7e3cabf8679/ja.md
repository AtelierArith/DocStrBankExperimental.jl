```
cube_field_size(cube::String)
```

与えられたキューブラベルのフィールドサイズを決定します。

この関数は、最初の出力パラメータ `pointdim` に環境空間の次元を返し、2 番目の戻り変数 `pointlen` に個々の座標フィールドの長さを返します。

# 例

```jldoctest
julia> cube_field_size("011654003020.0110")
(4, 3)
```

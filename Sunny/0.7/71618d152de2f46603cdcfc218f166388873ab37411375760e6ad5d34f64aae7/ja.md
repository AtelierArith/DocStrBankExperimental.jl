```
primitive_cell(cryst)
```

`cryst`の格子ベクトルの倍数での原始セルの形状。具体的には、`cryst.latvecs * primitive(cryst)`の列がグローバルな直交座標系での原始格子ベクトルを定義します。空間群設定情報が欠けている場合は`nothing`を返します。

この関数は、[`reshape_supercell`](@ref)への入力を構築するのに役立つかもしれません。

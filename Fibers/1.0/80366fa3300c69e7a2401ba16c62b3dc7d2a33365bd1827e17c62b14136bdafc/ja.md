```
xfm_apply(xfm::Xform{Tx}, point::Array{Ti})
```

`Xform`構造体で指定された変換を、長さ3*Nのボクセル座標配列で指定されたNポイントに適用し、変換されたポイントを入力配列と同じ形状のボクセル座標配列として返します。

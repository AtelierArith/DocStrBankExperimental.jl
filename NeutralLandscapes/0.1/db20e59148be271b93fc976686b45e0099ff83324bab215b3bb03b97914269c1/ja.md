```
EdgeGradient <: NeutralLandscapeMaker

EdgeGradient(; direction=360rand())
EdgeGradient(direction)
```

この型は、*x* および *y* 座標の双線形関数として値が変化するエッジグラデーションの風景を生成するために使用されます。方向は浮動小数点値として表現され、* [0,360]* の範囲にあります。内部コンストラクタは渡された値のモジュロを 360 で計算するため、正しい範囲外の値は修正されます。

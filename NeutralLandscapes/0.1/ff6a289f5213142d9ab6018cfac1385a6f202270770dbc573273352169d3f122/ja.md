```
PlanarGradient <: NeutralLandscapeMaker

PlanarGradient(; direction=360rand())
PlanarGradient(direction)
```

この型は、*x* および *y* 座標の双線形関数として値が変化する平面勾配の風景を生成するために使用されます。方向は浮動小数点値として表現され、* [0,360]* の範囲にあります。内部コンストラクタは渡された値のモジュロを 360 で計算するため、正しい区間を外れた値は修正されます。

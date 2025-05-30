```
interpolate(B, T, xi)
```

基底 B を与えられたとき、xi で T を補間します。

# 例

```jldoctest
B = Quad4()
X = Vec.([(0.0, 0.0), (1.0, 0.0), (1.0, 1.0), (0.0, 1.0)])
T = [1.0, 2.0, 3.0, 4.0]
interpolate(B, T, Vec(0.0, 0.0))

# 出力

2.5
```

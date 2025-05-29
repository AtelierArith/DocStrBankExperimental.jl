```
BoundedCylinder(radius::T, height::T; interface::NullOrFresnel{T} = nullinterface(T)) -> CSGGenerator{T}
```

両端に平面キャップがあり、中心が `(0, 0, 0)` で、軸が `(0, 0, 1)` の円柱を作成します。

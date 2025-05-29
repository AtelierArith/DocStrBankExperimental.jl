```
spatial_coordinate(fe_v::AbstractValues, q_point::Int, x::AbstractVector)
```

四分点での空間座標を計算します。`x` にはセルのノード座標が含まれています。

座標は、幾何学的補間を使用して計算されます。$\mathbf{x} = \sum\limits_{i = 1}^n M_i (\mathbf{\xi}) \mathbf{\hat{x}}_i$。

ここで、$\xi$は関連する四分法則の与えられた四分点 `q_point` の座標です。

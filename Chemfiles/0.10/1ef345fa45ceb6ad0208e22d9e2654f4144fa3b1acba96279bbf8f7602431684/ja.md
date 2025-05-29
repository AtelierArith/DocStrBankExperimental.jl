```julia
matrix(cell::Chemfiles.UnitCell) -> Matrix{Float64}

```

`cell`の行列表現を取得します。*すなわち*、3つの基底ベクトルの表現は次のようになります：

```
    | a_x   b_x   c_x |
    |  0    b_y   c_y |
    |  0     0    c_z |
```

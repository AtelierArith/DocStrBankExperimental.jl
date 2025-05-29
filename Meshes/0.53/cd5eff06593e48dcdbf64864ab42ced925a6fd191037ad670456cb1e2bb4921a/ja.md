```
Affine(A, b)
```

アフィン変換 `Ax + b` は、行列 `A` とベクトル `b` を使用します。

# 例

```julia
Affine(AngleAxis(0.2, 1.0, 0.0, 0.0), [-2, 2, 2])
Affine(Angle2d(π / 2), SVector(2, -2))
Affine([0 -1; 1 0], [-2, 2])
```

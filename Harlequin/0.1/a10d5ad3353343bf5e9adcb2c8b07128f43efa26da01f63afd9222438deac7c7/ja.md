```
rotationmatrix_normalized(q::Quaternion)
```

クォータニオン `q` によってエンコードされた回転を表す 3×3 行列を返します。この関数は、クォータニオンが正規化されていると仮定します。これは、`q` が `qrotation_x`、`qrotation_y`、および `qrotation_z` 関数を使用して構築された回転の合成である場合に該当します。

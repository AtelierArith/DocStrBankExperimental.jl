```
rotate_z(p::PVector, yaw::Number)
```

`p`をz軸周りに`yaw`ラジアンの角度で回転させます。回転方向は右手系で、y-z平面では反時計回りです。角度には単位を持たせることができます。例えば、u"°"（\degree）。

回転行列：

```
          | cos(yaw)  -sin(yaw)  0 |
Rz(yaw) = | sin(yaw)   cos(yaw)  0 |
          |    0          0      1 |
```

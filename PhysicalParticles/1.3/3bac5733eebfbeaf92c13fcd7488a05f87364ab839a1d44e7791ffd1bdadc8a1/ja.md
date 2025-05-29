```
rotate_x(p::PVector, roll::Number)
```

`p`をx軸周りに`roll`ラジアンの角度で回転させます。回転方向は右手系で、y-z平面では反時計回りです。角度には単位を持たせることができます。例えば、u"°"（\degree）。

回転行列：

```
           | 1      0          0      |
Rx(roll) = | 0  cos(roll)  -sin(roll) |
           | 0  sin(roll)   cos(roll) |
```

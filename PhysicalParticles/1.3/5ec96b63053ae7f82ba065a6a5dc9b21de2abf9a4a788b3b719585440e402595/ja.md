```
rotate_y(p::PVector, pitch::Number)
```

`p`をy軸周りに`pitch`ラジアンの角度だけ回転させます。回転方向は右手系で、y-z平面では反時計回りです。角度には単位を持たせることができます。例えば、u"°"（\degree）。

回転行列：

```
            |  cos(pitch)   0   sin(pitch) |
Ry(pitch) = |       0       1        0     |
            | -sin(pitch)   0   cos(pitch) |
```

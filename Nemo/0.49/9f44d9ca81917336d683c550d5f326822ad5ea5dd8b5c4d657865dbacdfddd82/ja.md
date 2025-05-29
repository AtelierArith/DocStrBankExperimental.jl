```
ball(x::RealFieldElem, y::RealFieldElem)
```

与えられたペア $(x, y) = (x_m \pm x_r, y_m \pm y_r)$ に対して、$x_m \pm (|x_r| + |y_m| + |y_r|)$ を囲む Arb ボールを構築します。

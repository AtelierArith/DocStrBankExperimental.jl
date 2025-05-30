```
anglebtw(x::Miller, y::Miller, g::MetricTensor)
anglebtw(x::MillerBravais, y::MillerBravais, g::MetricTensor)
anglebtw(x::ReciprocalMiller, y::ReciprocalMiller, g::MetricTensor)
anglebtw(x::ReciprocalMillerBravais, y::ReciprocalMillerBravais, g::MetricTensor)
```

2つの方向の間の角度（度単位）を計算するには：

$$
\cos\theta = \frac{\mathbf{x} \cdot \mathbf{y}}{\lvert\mathbf{x}\rvert \lvert\mathbf{y}\rvert}
             = \frac{\sum_{ij} x_i g_{ij} y_j}{\sqrt{\sum_{ij} x_i g_{ij} x_j} \sqrt{\sum_{ij} y_i g_{ij} y_j}}.
$$

!!! note
    2つの平面法線の間の角度については、結果は $180 - \theta$ です。


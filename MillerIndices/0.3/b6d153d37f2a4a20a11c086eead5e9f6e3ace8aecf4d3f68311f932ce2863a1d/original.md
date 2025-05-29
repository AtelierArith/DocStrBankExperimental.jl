```
anglebtw(x::Miller, y::Miller, g::MetricTensor)
anglebtw(x::MillerBravais, y::MillerBravais, g::MetricTensor)
anglebtw(x::ReciprocalMiller, y::ReciprocalMiller, g::MetricTensor)
anglebtw(x::ReciprocalMillerBravais, y::ReciprocalMillerBravais, g::MetricTensor)
```

Calculate the angle (in degrees) between two directions by:

$$
\cos\theta = \frac{\mathbf{x} \cdot \mathbf{y}}{\lvert\mathbf{x}\rvert \lvert\mathbf{y}\rvert}
             = \frac{\sum_{ij} x_i g_{ij} y_j}{\sqrt{\sum_{ij} x_i g_{ij} x_j} \sqrt{\sum_{ij} y_i g_{ij} y_j}}.
$$

!!! note
    For the angle between two plane normals, the result is $180 - \theta$.


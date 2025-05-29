```
PlaneSource(medium::P, amplitude::SVector, direction::SVector)
```

Is a struct type which describes a plane-wave source that drives/forces the whole system. It has three fields: a physical `medium`, an `amplitude` of the source, and the direction the propagate in `direction`.

For any given angular frequency ω, the PlaneSource has the value $e^{i ω/c \mathbf v \cdot \mathbf x }$ at the point $\mathbf x$, where $c$ is the medium wavespeed and $\mathbf v$ is the direction.

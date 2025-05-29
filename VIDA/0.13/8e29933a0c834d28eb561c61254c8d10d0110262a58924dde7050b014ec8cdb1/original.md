```julia
struct Bhattacharyya <: VIDA.AbstractDivergence
```

Type for the Bhattacharyya divergence. It constructed from an `IntensityMap` i.e. data. Additionally to evaluate the divergence we use a functor approach where if θ is your

### Details

This computes the Bhattacharyya divergence which is related to Hellinger distance between two distributions. In fact, they are both minimized at the same point. The Bhattacharyya divergence is defined as

$$
Bh(f_\theta||\hat{I}) = -\log\int \sqrt{f_\theta(x,y)\hat{I}(x,y)}dxdy,
$$

where $\hat{I}$ is defined as the image normalized to unit flux.

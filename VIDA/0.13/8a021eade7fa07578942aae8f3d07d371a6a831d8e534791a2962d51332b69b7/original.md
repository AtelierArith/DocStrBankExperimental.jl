```julia
struct KullbackLeibler <: VIDA.AbstractDivergence
```

Type for the KL divergence. It constructed from an `IntensityMap` i.e. data. Additionally to evaluate the divergence we use a functor approach where if θ is your

### Details

This computes the KL divergence which is related to Hellinger distance between two distributions. In fact, they are both minimized at the same point. The Bhattacharyya divergence is defined as

$$
KL(f_\theta||\hat{I}) = -\log\int f_{\theta}(x,y)\log
        \left(\frac{f_{\theta}(x,y)}{\hat{I}(x,y)}\right)dxdy,
$$

where $\hat{I}$ is defined as the image normalized to unit flux.

This struct is also a functor.

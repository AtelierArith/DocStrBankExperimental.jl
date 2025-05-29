```
Renyi(img::IntensityMap, α)
```

Construct the Renyi divergence with parameter α. It constructed from an `IntensityMap` i.e. data.

### Details

This computes the KL divergence which is related to Hellinger distance between two distributions. In fact, they are both minimized at the same point. The Bhattacharyya divergence is defined as

$$
Ry(f_\theta||\hat{I}) = \frac{1}{α-1}\log\int
        \left(\frac{f_{\theta}(x,y)^\alpha}{\hat{I}(x,y)^{\alpha-1}}\right)dxdy,
$$

where $\hat{I}$ is defined as the image normalized to unit flux.

This is a very flexible divergence that reduces to many of the other divergences implemented.

  * `α = 1` corresponds to the KL divergence
  * `α = 1/2` corresponds to the Bhattacharyya divergence up to a multiplicative factor of 2

Typically we find that `α=1.5` works well, as it focusses on the bright regions of the images moreso than the Bh and KL divergence. For `α>2` the measure tends to devolve in something akin the to sup norm and fails to match the image structure.

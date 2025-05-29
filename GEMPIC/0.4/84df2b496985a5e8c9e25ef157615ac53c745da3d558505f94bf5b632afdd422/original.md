```
sample!( pg::ParticleGroup{1,1}, α, k, σ, mesh::OneDGrid)
```

Sampling from a probability distribution to initialize a Landau damping in 1D1V space.

$$
f_0(x,v,t) = \frac{n_0}{\sqrt{2π} v_{th}} ( 1 + \alpha cos(k_x x)) exp( - \frac{v^2}{2 v_{th}^2})
$$

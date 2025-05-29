```
kernel(::ContinuousHistogram, ::AbstractArray, data) -> MethodError
kernel(::GaussianHistogram, ::AbstractArray, data)
kernel(::UniformHistogram, ::AbstractArray, data)
```

The kernel function $\mathcal{K}(x)$ used to compute a [`ContinuousHistogram`](@ref) such that

$$
\mathcal{H}(x) = \sum_{i = 1}^M \mathcal{K}_i(x),
$$

where $M$ is the total number of data points. For brevity, we have represented all `data`-dependence through the subscript $i$. 

!!! note
    By default, we `MethodError` out for any `<: ContinuousHistogram` until its directly implemented.


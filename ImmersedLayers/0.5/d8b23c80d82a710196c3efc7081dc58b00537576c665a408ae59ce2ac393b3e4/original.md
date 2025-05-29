```
create_surface_filter(cache::BasicILMCache)
```

Create a surface filtering matrix operator $\tilde{R}^T R$, where $\tilde{R}^T$ represents a modified version of the interpolation operator. The resulting matrix can be applied to surface data to filter out high-frequency components.

```
flux(T::Tensor)
```

Return the flux of a Tensor, based on what non-zero blocks it has. If the Tensor is not blocked or has no non-zero blocks, this function returns `nothing`.

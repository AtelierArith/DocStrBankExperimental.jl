```
AI2Box <: AI2
```

AI2 forward algorithm for ReLU activation functions based on abstract interpretation with the interval domain from [GehrMDTCV18](@citet).

### Notes

This algorithm is less precise than [`BoxForward`](@ref) because it abstracts after every step, including the affine map.

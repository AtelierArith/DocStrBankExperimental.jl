```
real_dimension(𝔽::AbstractNumbers)
```

Return the real dimension $\dim_ℝ 𝔽$ of the [`AbstractNumbers`](@ref) system `𝔽`. The real dimension is the dimension of a real vector space with which a number in `𝔽` can be identified. For example, [`ComplexNumbers`](@ref) have a real dimension of 2, and [`QuaternionNumbers`](@ref) have a real dimension of 4.

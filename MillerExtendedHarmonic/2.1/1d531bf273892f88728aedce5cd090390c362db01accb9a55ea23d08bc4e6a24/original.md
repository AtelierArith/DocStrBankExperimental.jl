```
flat_coeffs!(flat::AbstractVector{<:Real}, mxh::MXH)
```

return all mxh coefficients as an array of floats of length 5 + 2L where L is the number of sin/cos coefficients

NOTE: operates in place on `flat` input vector and is not autodiff compatible

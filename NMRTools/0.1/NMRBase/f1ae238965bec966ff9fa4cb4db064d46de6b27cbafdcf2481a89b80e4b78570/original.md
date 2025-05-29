```
setgradientlist(A::NMRData, [dimnumber], relativegradientlist, Gmax=nothing)
```

Return a new NMRData with a gradient axis containing the passed values. If no maximum strength is specified, a default gradient strength of 0.55 T m⁻¹ will be set, but a warning raised for the user.

If a dimension number is specified, that dimension will be replaced. If not, the function will search for a unique non-frequency dimension, and replace that. If there are multiple non-frequency dimensions, the dimension number must be specified explicitly, and the function will throw an error.

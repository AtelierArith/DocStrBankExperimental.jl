```
Distribution{F<:VariateForm,S<:ValueSupport} <: Sampleable{F,S}
```

`Distribution` is a `Sampleable` generating random values from a probability distribution. Distributions define a Probability Distribution Function (PDF) to implement with `pdf` and a Cumulative Distribution Function (CDF) to implement with `cdf`.

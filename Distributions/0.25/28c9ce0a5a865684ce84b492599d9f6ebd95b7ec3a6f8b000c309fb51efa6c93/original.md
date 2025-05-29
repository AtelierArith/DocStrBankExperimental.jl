```
Sampleable{F<:VariateForm,S<:ValueSupport}
```

`Sampleable` is any type able to produce random values. Parametrized by a `VariateForm` defining the dimension of samples and a `ValueSupport` defining the domain of possibly sampled values. Any `Sampleable` implements the `Base.rand` method.

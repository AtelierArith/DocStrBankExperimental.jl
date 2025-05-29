```
compute_Mlincomb_from_MM(nep::NEP,λ::Number,V,a)
```

This function provides a `compute_Mlincomb`-function call  by invoking a call to `compute_MM`. The underlying mathematical relationship  is described in github issue #2 and #3.

The standard usage is by the following command:

```julia
compute_Mlincomb(nep::MyNEP,λ::Number,V,a)=compute_Mlincomb_from_MM(nep,λ,V,a)
```

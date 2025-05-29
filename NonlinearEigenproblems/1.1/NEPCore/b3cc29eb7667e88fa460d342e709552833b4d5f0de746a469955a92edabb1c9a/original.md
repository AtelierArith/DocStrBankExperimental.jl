```
compute_Mlincomb_from_Mder(nep::NEP,λ::Number,V,a)
```

The function computes `Mlincomb` by a call to `compute_Mder`. This function is slow since it requires the construction of the matrices. Usage normally by overloading in this way

```julia
    compute_Mlincomb(nep::MyNEP,λ::Number,V,a)=compute_Mlincomb_from_Mder(nep,λ,V,a)
```

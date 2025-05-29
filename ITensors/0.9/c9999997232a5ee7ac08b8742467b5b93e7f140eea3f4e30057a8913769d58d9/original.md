```
checkflux(T::Tensor, flux)
```

Check that fluxes of all non-zero blocks of a blocked or symmetric Tensor equal the value `flux`. Throws an error if one or more blocks does not have this flux.

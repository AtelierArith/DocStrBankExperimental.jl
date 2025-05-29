```
checkflux(T::Tensor)
```

Check that fluxes of all non-zero blocks of a blocked or symmetric Tensor are equal. Throws an error if one or more blocks have a different flux. If the tensor is dense (is not blocked) then `checkflux` returns `nothing`.

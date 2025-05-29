```
CroppingOperator(outdims, inpdims, offset=defaultoffset(outdims,inpdims))
```

yields a linear map which implements cropping of arrays of size `inpdims` to produce arrays of size `outdims`.  By default, the output array is centered with respect to the inpput array (using the same conventions as `fftshift`). Optional argument `offset` can be used to specify a different relative position.  If `offset` is given, the output value at multi-dimensional index `i` is given by input value at index `j = i + offset`.

The adjoint of a cropping operator is a zero-padding operator.

See also: [`ZeroPaddingOperator`](@ref).

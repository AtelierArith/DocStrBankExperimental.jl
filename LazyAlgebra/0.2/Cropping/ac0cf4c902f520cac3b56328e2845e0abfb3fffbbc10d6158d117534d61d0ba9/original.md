```
ZeroPaddingOperator(outdims, inpdims, offset=defaultoffset(outdims,inpdims))
```

yields a linear map which implements zero-padding of arrays of size `inpdims` to produce arrays of size `outdims`.  By default, the input array is centered with respect to the output array (using the same conventions as `fftshift`). Optional argument `offset` can be used to specify a different relative position.  If `offset` is given, the input value at multi-dimensional index `j` is copied at index `i = j + offset` in the result.

A zero-padding operator is implemented as the adjoint of a cropping operator.

See also: [`CroppingOperator`](@ref).

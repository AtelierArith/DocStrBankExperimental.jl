```
remove_padding(m, nb; true_adjoint=False)
```

Removes the padding from array `m`. This is the adjoint of [`pad_array`](@ref).

Parameters

  * `m`: Array to remvove padding from.
  * `nb`: Size of padding. Array of tuple with one (nb*left, nb*right) tuple per dimension.
  * `true_adjoint`: Unpadding mode, defaults to False. Will sum the padding to the edge point with `true_adjoint=true`

and should only be used this way for adjoint testing purpose.

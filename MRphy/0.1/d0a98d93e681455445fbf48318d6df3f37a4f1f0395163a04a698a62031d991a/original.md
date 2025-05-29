```
UΦRot!(U, Φ, V, R)
```

Apply axis-angle, `U`-`Φ` based rotation on `V`. Rotation is broadcasted on `V` along its 3rd dimension. Results will overwrite into `R`.

*INPUTS*:

  * `U::TypeND(AbstractFloat,[2])` (nM, 3), rotation axes in 3D, assumed unitary;
  * `Φ::TypeND(AbstractFloat,[1])` (nM,), rotation angles;
  * `V::TypeND(AbstractFloat,[2,3])` (nM, 3, (3)), vectors to be rotated;
  * `R::TypeND(AbstractFloat,[2,3])` (nM, 3, (3)), vectors rotated, i.e., results;

*OUTPUTS*:

  * `R` the input container `R` is also returned for convenience.

See also: [`UΦRot`](@ref), [`B2UΦ!`](@ref).

```
function setaffine(h::NIfTIHeader, affine::Array{T,2}) where {T}
```

Set the affine of a `NIfTIHeader` to 4x4 affine matrix `affine`

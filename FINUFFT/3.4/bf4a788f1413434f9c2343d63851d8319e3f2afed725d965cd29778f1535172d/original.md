```
output::Array{Complex{T}} = finufft_exec(plan::finufft_plan{T},
                  input::FINUFFT.InputArray{Complex{T}}) where T <: finufftReal
```

Execute single or many-vector FINUFFT transforms in a plan.

output = finufft_exec(plan, input)

For `plan` a previously created `finufft_plan` object also containing all needed   nonuniform point coordinates, do a single (or if `ntrans>1` in the plan stage, multiple)   NUFFT transform(s), with the strengths or Fourier coefficient inputs vector(s) from   `input`. The result of the transform(s) is returned as a (possibly multidimensional)   array.

# Inputs

```
- `plan`    `finufft_plan` object, already planned and containing nonuniform points.
- `input`   strengths (types 1 or 3) or Fourier coefficients (type 2) vector, matrix,
            or array of appropriate size. For type 1 and 3, this is either a length-M
            vector (where M is the length of `xj`), or an `(M,ntrans)` matrix when
            `ntrans>1`. For type 2, in 1D this is size `(ms,)`, in 2D size `(ms,mt)`,
            or in 3D size `(ms,mt,mu)`, or each of these with an extra last dimension
            `ntrans` if `ntrans>1`.
            Must be contiguous.
```

# Output

```
 `output`   vector of output strengths at targets (types 2 or 3), or array of Fourier
            coefficients (type 1), or, if `ntrans>1`, a stack of such vectors or
            arrays, of appropriate size.  Specifically, if `ntrans=1`, for type 1, in
            1D this is size `(ms,)`, in 2D size `(ms,mt)`, or in 3D size `(ms,mt,mu)`;
            for types 2 and 3 it is a column vector of length `M` (the length of `xj`
            in type 2), or `nk` (the length of `s` in type 3). If `ntrans>1` it is a
            stack of such objects, ie, it has an extra last dimension `ntrans`.
```

```
primitivize(flat::AbstractFourierLattice, cntr::Char) --> ::typeof(flat)
```

Given `flat` referred to a conventional basis with centering `cntr`, compute the derived (but physically equivalent) lattice `flat′` referred to the associated primitive basis. 

Specifically, if `flat` refers to a direct conventional basis `Rs` $≡ (\mathbf{a} \mathbf{b} \mathbf{c})$ [with coordinate vectors $\mathbf{r} ≡ (r_1, r_2, r_3)^{\mathrm{T}}$] then `flat′` refers to a direct primitive basis `Rs′` $≡ (\mathbf{a}' \mathbf{b}' \mathbf{c}') ≡ (\mathbf{a} \mathbf{b} \mathbf{c})\mathbf{P}$ [with coordinate vectors  $\mathbf{r}' ≡ (r_1', r_2', r_3')^{\mathrm{T}} = \mathbf{P}^{-1}\mathbf{r}$], where $\mathbf{P}$ denotes the basis-change matrix obtained from `primitivebasismatrix(...)`.

To compute the associated primitive basis vectors, see [`primitivize(::DirectBasis, ::Char)`](@ref) [specifically, `Rs′ = primitivize(Rs, cntr)`].

## Examples

A centered ('c') lattice from plane group 5 in 2D, plotted in its  conventional and primitive basis (requires `using PyPlot`):

```julia-repl
julia> sgnum = 5; D = 2; cntr = centering(sgnum, D)  # 'c' (body-centered)

julia> Rs   = directbasis(sgnum, Val(D))     # conventional basis (rectangular)
julia> flat = levelsetlattice(sgnum, Val(D)) # Fourier lattice in basis of Rs
julia> flat = modulate(flat)                 # modulate the lattice coefficients
julia> plot(flat, Rs)

julia> Rs′   = primitivize(Rs, cntr)    # primitive basis (oblique)
julia> flat′ = primitivize(flat, cntr)  # Fourier lattice in basis of Rs′

julia> using PyPlot
julia> plot(flat′, Rs′)
```

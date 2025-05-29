```
primitivebasismatrix(cntr::Char, ::Val{D}=Val(3)) --> SMatrix{D,D,Float64}
primitivebasismatrix(cntr::Char, ::Val{D}, ::Val{P}) --> SMatrix{D,D,Float64}
```

Return the transformation matrix $\mathbf{P}$ that transforms a conventional unit cell with centering `cntr` to the corresponding primitive unit cell (in dimension `D` and periodicity `P`) in CDML setting.

If `P` is not provided, it default to `D` (as e.g., applicable to Crystalline.jl's  `spacegroup`). If `D` and `P` differ, a subperiodic group setting is assumed (as e.g., applicable to Crystalline.jl's `subperiodicgroup`).

## Transformations in direct and reciprocal space

### Bases

The returned transformation matrix $\mathbf{P}$ transforms a direct-space conventional basis $(\mathbf{a}\ \mathbf{b}\ \mathbf{c})$ to the direct-space primitive basis

$$
    (\mathbf{a}'\ \mathbf{b}'\ \mathbf{c}') =
    (\mathbf{a}\ \mathbf{b}\ \mathbf{c})\mathbf{P}.
$$

Analogously, $\mathbf{P}$ transforms a reciprocal-space conventional basis $(\mathbf{a}^*\ \mathbf{b}^*\ \mathbf{c}^*)$ to 

$$
(\mathbf{a}^{*\prime}\ \mathbf{b}^{*\prime}\ \mathbf{c}^{*\prime}) =
(\mathbf{a}^*\ \mathbf{b}^*\ \mathbf{c}^*)(\mathbf{P}^{-1})^{\text{T}}.
$$

see also [`transform(::DirectBasis, ::AbstractMatrix{<:Real})`](@ref) and [`transform(::ReciprocalBasis, ::AbstractMatrix{<:Real})`](@ref)).

### Coordinates

The coordinates of a point in either direct or reciprocal space, each referred to a basis, also transform under $\mathbf{P}$. Concretely, direct- and reciprocal-space conventional points $\mathbf{r} = (r_1, r_2, r_3)^{\text{T}}$ and $\mathbf{k} = (k_1, k_2, k_3)^{\text{T}}$, respectively, transform to a primitive setting under $\mathbf{P}$ according to:

$$
\mathbf{r}' = \mathbf{P}^{-1}\mathbf{r},\\
\mathbf{k}' = \mathbf{P}^{\text{T}}\mathbf{k}.
$$

See also [`transform(::DirectPoint, ::AbstractMatrix{<:Real})`](@ref) and [`transform(::ReciprocalPoint, ::AbstractMatrix{<:Real})`](@ref)).

## Setting conventions

The setting choice for the primitive cell implied by the returned $\mathbf{P}$ follows the widely adopted Cracknell-Davies-Miller-Love (CDML) convention.[^CDML] This convention is explicated e.g. in Table 2 of [^Aroyo] (or, alternatively, can be inferred from Tables 1.5.4.1 and 1.5.4.2 of [^ITB2]) and is followed e.g. on the Bilbao Crystallographic Server[^BCS], in the CDML reference work on space group irreps[^CDML], and in the C library `spglib`.[^spglib]

Note that this setting choice is *not* what is frequently referred to as the "ITA primitive setting", from which it differs for hP, hR, and oA Bravais types.

The setting choice is usually referred to as the CDML primitive setting, or, less frequently and more ambiguously, as the crystallographic primitive setting.

[^CDML]: Cracknell, Davies, Miller, & Love, Kroenecker Product Tables, Vol. 1 (1979).

[^BCS]: Bilbao Crystallographic Server, [KVEC](https://www.cryst.ehu.es/cryst/get_kvec.html).

[^Aroyo]: Aroyo *et al.*, [Acta Cryst. A70, 126 (2014)](https://doi.org/10.1107/S205327331303091X): Table 2 gives       $(\mathbf{P}^{-1})^{\text{T}}$.

[^ITB2]: Hahn, International Tables of Crystallography, Vol. B, 2nd edition (2001).

[^spglib]: Spglib documentation: [Transformation to the primitive setting](https://spglib.github.io/spglib/definition.html#transformation-to-the-primitive-cell).        Thus, Bravais.jl and [Spglib.jl](https://github.com/singularitti/Spglib.jl)        transform to identical primitive settings and are hence mutually compatible.

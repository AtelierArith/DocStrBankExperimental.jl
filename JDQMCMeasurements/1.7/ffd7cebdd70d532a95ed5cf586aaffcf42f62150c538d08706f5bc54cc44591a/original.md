```
fourier_transform!(
    C::AbstractArray{Complex{T}},
    a::Int,
    b::Int,
    dims,
    unit_cell::UnitCell{D,T},
    lattice::Lattice{D}
) where {D, T<:AbstractFloat}

fourier_transform!(C::AbstractArray{Complex{T}},
    a::Int,
    b::Int,
    unit_cell::UnitCell{D,T},
    lattice::Lattice{D}
) where {D, T<:AbstractFloat}
```

Calculate the fourier transform from position to momentum space

$$
\begin{align*}
C_{\mathbf{k}}^{a,b}= & \sum_{\mathbf{r}}e^{{\rm -i}\mathbf{k}\cdot(\mathbf{r}+\mathbf{r}_{a}-\mathbf{r}_{b})}C_{\mathbf{r}}^{a,b}
\end{align*}
$$

where $a$ and $b$ specify orbital species in the unit cell. Note that the array `C` is modified in-place. If `dims` is passed, iterate over these dimensions of the array, performing a fourier transform on each slice.

```
local_update_greens!(
    G::AbstractMatrix{T}, logdetG::E, sgndetG::T,
    B::AbstractPropagator{T},
    R::T, Δ::F, i::Int,
    u::AbstractVector{T}, v::AbstractVector{T}
)::Tuple{E,T} where {T<:Number, F<:Number, E<:AbstractFloat}
```

Update the equal-time Green's function matrix `G` resulting from a local update in-place.

# Arguments

  * `G::AbstractMatrix{T}`: Equal-time Green's function matrix $G(\tau,\tau)$ that will be updated in-place.
  * `logdetG::E`: The log of the absolute value of the initial Green's function matrix, $\log( \vert \det G(\tau,\tau) \vert ).$
  * `sgndetG::T`: The sign/phase of the determinant of the initial Green's function matrix, $\textrm{sign}( \det G(\tau,\tau) ).$
  * `B::AbstractPropagator{T,E}`: Propagator that needs to be updated to reflect accepted local update.
  * `R::T`: The determinant ratio $R_{l,i} = \frac{\det G(\tau,\tau)}{\det G^\prime(\tau,\tau)}.$
  * `Δ::F`: Change in the exponentiated on-site energy matrix, $\Delta_{l,i} = e^{-\Delta\tau (V^\prime_{l,(i,i)} - V_{l,(i,i)})} - 1.$
  * `i::Int`: Matrix element of diagonal on-site energy matrix $V_l$ that is being updated.
  * `u::AbstractVector{T}`: Vector of length `size(G,1)` that is used to avoid dynamic memory allocations.
  * `v::AbstractVector{T}`: Vector of length `size(G,2)` that is used to avoid dynamic memory allocations.

# Algorithm

The equal-time Green's function matrix is updated using the relationship

$$
G_{j,k}^{\prime}\left(\tau,\tau\right)=G_{j,k}\left(\tau,\tau\right)-\frac{1}{R_{l,i}}G_{j,i}\left(\tau,\tau\right)\Delta_{l,i}\left(\delta_{i,k}-G_{i,k}\left(\tau,\tau\right)\right).
$$

The  $B_l$ progpagator `B` is also udpated. Additionally, this method returns $\log( \vert \det G^\prime(\tau,\tau) \vert )$ and $\textrm{sign}( \det G^\prime(\tau,\tau) ).$

An important note is that if the propagator matrices are represented in a symmetric form, then `G′` and `G` need to correspond to the transformed eqaul-time Green's function matrices $\tilde{G}^\prime(\tau,\tau)$ and $\tilde{G}(\tau,\tau).$ Refer to the [`local_update_det_ratio`](@ref) docstring for more information.

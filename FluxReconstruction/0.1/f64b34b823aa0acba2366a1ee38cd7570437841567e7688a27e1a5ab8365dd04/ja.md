```julia
struct UnstructFRPSpace{A, H, G<:Integer, B<:(AbstractMatrix{<:AbstractFloat}), F<:(AbstractArray{<:AbstractFloat, 3}), E<:(AbstractVector{<:AbstractFloat}), I<:(AbstractArray{<:AbstractFloat, 4}), J} <: FluxReconstruction.AbstractUnstructFRSpace
```

フラックス再構成法のための非構造物理空間

# フィールド

  * `base`
  * `J`
  * `deg`
  * `np`
  * `xpl`
  * `xpg`
  * `wp`
  * `xfl`
  * `xfg`
  * `wf`
  * `V`
  * `ψf`
  * `Vr`
  * `Vs`
  * `∂l`
  * `lf`
  * `ϕ`
  * `fpn`

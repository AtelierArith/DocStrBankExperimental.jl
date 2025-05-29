fit!(uf::UnfoldModel,data::Union{<:AbstractArray{T,2},<:AbstractArray{T,3}}) where {T<:Union{Missing, <:Number}}

Fit a DesignMatrix against a 2D/3D Array data along its last dimension Data is typically interpreted as channel x time (with basisfunctions) or channel x time x epoch (for mass univariate)

  * `show_progress` (default:true), deactivate the progressmeter

Returns an UnfoldModel object

# Examples

```julia-repl

```

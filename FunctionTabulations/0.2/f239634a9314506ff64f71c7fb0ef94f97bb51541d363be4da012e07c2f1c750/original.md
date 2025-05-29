```
create_tabulation_1D(
    func::Function[,
    args...];
    xmin::T,
    xmax::T,
    npoints::Int[,
    x_scale::Symbol = :linear,
    f_scale = :linear,
    jld_base_path = nothing,
    custom_name = nothing,
    interpolation_type = :linear,
    extrapolation_bc = Throw,
    check_SHA = true,
    check_SHA_mode = :warn,
    metadata=nothing,
    metadata_validation_fn=nothing,
    kwargs...]
) where {T<:Union{Real,Quantity}}
```

Computes or loads the tabulation for a given function of the kind `f(x)`.

# Arguments

  * `func::Function`: the function which should be tabulated. Must be of the kind `f(x)`
  * `xmin::Union{Real,Quantity}`: the minimum `x` for the range which will be covered by the tabulation
  * `xmax::Union{Real,Quantity}`: the maximum `x` for the range which will be covered by the tabulation
  * `npoints::Int`: the number of points for which `f(x)` will be computed
  * `x_scale::Symbol`: the scale which will be used for tabulation. If `:linear` is choosen, the `x` points will be evenly spaced. If `:log10` is chosen, the points will be logarithmically spaced. Defaults to `:linear`
  * `f_scale::Symbol`: the scale which will be used for tabulation. If `:linear` is choosen, the `f(x)` points will not be alterated. If `:log10` is chosen, log10 will be applied to the `f(x)` points before interpolating. Defaults to `:linear`
  * `jld_base_path::String`: path to the folder where the tabulation should be saved. Defaults to the current folder
  * `custom_name::String`: custom name for the tabulation file, to which `_data.jld2` will be appended. Defaults to the name of the function to be tabulated
  * `interpolation_type::Symbol`: Type of the spline to be used for interpolation. Can either be :linear (1st order spline) or :cubic (3rd order spline)
  * `extrapolation_bc`: behaviour of the tabulation outside of the boundaries defined by `[xmin, xmax]`. Possible behaviours are handled by Interpolations.jl and include `Throw``(throws and eror if a value out of bounds is acessed) or`Line`(extrapolate linearly). Defaults to`Throw`
  * `check_SHA::Bool`: Whether to check the SHA of the tabulated function. If the SHA of the tabulated function does not match the SHA stored inside the tabulation file, it might be necessary to recompute the tabulation, since it's likely that the definition of the tabulated function has changed.
  * `check_SHA_mode::Symbol`: Describes the behaviour of this function if the SHA of the tabulated function does not match the SHA stored inside the tabulation file. Defaults to :warn (print a warning but load the tabulation all the same). Other options include :throw (throw an error to suggest manual deletion of the old tabulation) and :none (don't do anything).
  * `metadata::Dict{String,Any}`: an optional `Dict{String, Any}` which contains additional metadata to be stored in the tabulation achive.
  * `metadata_validation_fn::Function`: a function of the kind `metadata_validation_fn(metadata1::Dict{String, Any}, metadata2::Dict{String, Any})` to chech whether two metadata dictionaries contain the same data.
  * `args..., kwargs...`: additional `args` and `kwargs` will be passed to the function which is to be tabulated

# Examples

```jldoctest
julia>  func_1d(x) = sin(x)

julia>  itp_1d_1 = create_tabulation_1D(
            func_1d,
            xmin = 0.0,
            xmax = 3.0,
            npoints = 100,
            x_scale = :linear,
            f_scale = :linear
        )

julia>  isapprox(itp_1d_1(2.0), func_1d(2.0), rtol = 1e-3)
true
```

Measurement units are supported too:

```jldoctest
julia>  using Unitful

julia>  func_1d(x) = x^2

julia>  itp_1d_1 = create_tabulation_1D(
            func_1d,
            xmin = 0.0u"m",
            xmax = 3.0u"m",
            npoints = 100,
            x_scale = :linear,
            f_scale = :linear
        )

julia>  isapprox(itp_1d_1(2.0u"m"), func_1d(2.0u"m"), rtol = 1e-3)
true
```

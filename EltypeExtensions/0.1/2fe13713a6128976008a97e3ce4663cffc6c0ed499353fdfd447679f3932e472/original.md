```
convert_precisiontype(T::Type, A, prec)
```

Convert `A` to have the [`precisiontype`](@ref) of `T`. `prec` is optional.

  * When `T` has static precision (e.g. `Float64`), `prec` has no effect.
  * When `T` has dynamic precision (e.g. `BigFloat`), `prec` specifies the precision of conversion. When `prec` is not provided, the precision is decided by the external setup from `T`.
  * When `T` is an integer, the conversion will dig into `Rational` as well. In contrast, since `Rational` as a whole is more "precise" than an integer, [`precisiontype`](@ref) doesn't unwrap `Rational`.

# Examples

```jldoctest; setup = :(using EltypeExtensions: convert_precisiontype)
julia> convert_precisiontype(BigFloat, 1//3+im, 128)
0.3333333333333333333333333333333333333338 + 1.0im

julia> convert_precisiontype(Float16, [[m/n for n in 1:3] for m in 1:3])
3-element Vector{Vector{Float16}}:
 [1.0, 0.5, 0.3333]
 [2.0, 1.0, 0.6665]
 [3.0, 1.5, 1.0]
```

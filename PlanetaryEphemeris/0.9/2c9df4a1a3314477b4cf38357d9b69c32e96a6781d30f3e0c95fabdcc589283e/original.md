```
(tinterp::TaylorInterpolant{T, U, 1})(t::T) where {T, U}
(tinterp::TaylorInterpolant{T, U, 1})(t::TT) where {T, U, TT<:TaylorInterpCallingArgs{T,U}}
(tinterp::TaylorInterpolant{T, U, 2})(t::T) where {T, U}
(tinterp::TaylorInterpolant{T, U, 2})(t::TT) where {T, U, TT<:TaylorInterpCallingArgs{T,U}}
```

Evaluate `tinterp.x` at time `t`.

See also [`getinterpindex`](@ref).

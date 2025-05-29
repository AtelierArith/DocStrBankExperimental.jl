```
(tinterp::TaylorInterpolant{T, U, 1})(t::T) where {T, U}
(tinterp::TaylorInterpolant{T, U, 1})(t::TT) where {T, U, TT<:TaylorInterpCallingArgs{T,U}}
(tinterp::TaylorInterpolant{T, U, 2})(t::T) where {T, U}
(tinterp::TaylorInterpolant{T, U, 2})(t::TT) where {T, U, TT<:TaylorInterpCallingArgs{T,U}}
```

`tinterp.x`を時間`t`で評価します。

詳細は[`getinterpindex`](@ref)を参照してください。

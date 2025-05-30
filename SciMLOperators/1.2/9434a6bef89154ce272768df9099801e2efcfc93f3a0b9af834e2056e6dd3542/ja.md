```julia
has_expmv!(L)

```

`expmv!(w, L, v, t)`、すなわち `mul!(w, exp(t * A), v)` が、適切なサイズの `Number` `t` と `AbstractArray` `w, v` に対して定義されているかを確認します。

```
eval_dynamics(m::AbstractMachine, u::AbstractVector, x:AbstractVector{F}, p, t) where {F<:Function}
eval_dynamics(m::AbstractMachine{T}, u::AbstractVector, x:AbstractVector{T}, p, t) where T
```

マシン `m` の状態 `u`、パラメータ `p` および時間 `t` におけるダイナミクスを評価します。外生変数は `x` によって設定され、これは関数 $x_i(t)$ のコレクションまたは定数値のコレクションである可能性があります。いずれの場合も、`x` の長さは `m` への入力の数と等しくなければなりません。

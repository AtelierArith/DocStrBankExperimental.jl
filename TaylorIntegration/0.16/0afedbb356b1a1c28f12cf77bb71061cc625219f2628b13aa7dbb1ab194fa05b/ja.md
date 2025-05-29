```
lyap_taylorinteg(f!, q0, t0, tmax, order, abstol[, jacobianfunc!=nothing];
    maxsteps::Int=500, parse_eqs::Bool=true)
lyap_taylorinteg(f!, q0, trange, order, abstol[, jacobianfunc!=nothing];
    maxsteps::Int=500, parse_eqs::Bool=true)
```

[`taylorinteg`](@ref)と同様に、リャプノフスペクトルの計算に使用されます。`TaylorN`変数の数は、ユーザーによって事前に設定される必要があります（例えば、`TaylorSeries.set_variables`を使用して）し、初期条件ベクトル`q0`の長さと等しくなければなりません。そうでない場合、`length(q0) != TaylorSeries.get_numvars()`のとき、`lyap_taylorinteg`は`AssertionError`をスローします。オプションとして、ユーザーは現在のヤコビ行列の値を評価するためにヤコビ行列関数`jacobianfunc!`を提供することができます。そうでない場合、現在のヤコビ行列の値は`TaylorSeries.jl`を使用して自動微分によって計算されます。

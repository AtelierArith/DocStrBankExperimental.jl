```julia
halo(μ, lagrange; amplitude, phase, hemisphere, kwargs...)

```

!!! warning "CR3BP ダイナミクス"
    この計算は円形制限三体問題のダイナミクスに対して有効です。


無次元質量パラメータ `μ` と軌道特性を考慮して、リチャードソンの解析解を使用して初期推定を構築し、その推定を微分補正器を使用して反復します。

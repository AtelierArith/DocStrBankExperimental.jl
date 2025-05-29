```julia
halo(x, z, ẏ, μ, T; reltol, abstol, maxiters)

```

!!! warning "CR3BP ダイナミクス"
    この計算は円形制限三体問題のダイナミクスに対して有効です。


ハロ軌道条件の初期推定値を反復します。

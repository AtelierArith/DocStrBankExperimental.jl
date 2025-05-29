```julia
lyapunov(x, ẏ, μ, T; reltol, abstol, maxiters)

```

!!! warning "CR3BPダイナミクス"
    この計算は円形制限三体問題のダイナミクスに対して有効です。


リヤプノフ軌道条件の初期推定値を反復します。

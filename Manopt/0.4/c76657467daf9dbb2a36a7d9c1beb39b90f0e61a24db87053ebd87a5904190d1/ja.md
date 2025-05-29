```
update_hessian!(d, amp, st, p_old, iter)
```

[`QuasiNewtonState`](@ref) `o`内でHessianを更新します。`amp`は[`AbstractManoptProblem`](@ref)であり、`d`は[`AbstractQuasiNewtonDirectionUpdate`](@ref)で、最後の反復は`p_old`です。現在の（`iter`番目の）反復はすでに`o.x`に保存されています。

`d`内で利用可能な異なるルールについては、[`AbstractQuasiNewtonUpdateRule`](@ref)も参照してください。

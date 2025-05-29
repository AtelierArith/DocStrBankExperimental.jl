```
update_hessian!(d::AbstractQuasiNewtonDirectionUpdate, amp, st, p_old, k)
```

[`QuasiNewtonState`](@ref) `st`内のヘッセ行列を、[`AbstractManoptProblem`](@ref) `amp`および[`AbstractQuasiNewtonDirectionUpdate`](@ref) `d`と最後の反復値`p_old`を考慮して更新します。現在の（`k`番目の）反復値はすでに[`get_iterate`](@ref)`(st)`に保存されています。

また、`d`内で利用可能な異なるルールについては、[`AbstractQuasiNewtonUpdateRule`](@ref)およびそのサブタイプも参照してください。

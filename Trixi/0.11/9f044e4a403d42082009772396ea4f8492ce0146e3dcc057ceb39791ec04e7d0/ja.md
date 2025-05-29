```
EulerAcousticsCouplingCallback(ode_euler,
                               averaging_callback::DiscreteCallback{<:Any, <:AveragingCallback},
                               alg, cfl_acoustics::Real, cfl_euler::Real; kwargs...)
```

!!! warning "実験的なコード"
    このコールバックは実験的であり、将来のリリースで変更される可能性があります。


[`EulerAcousticsCouplingCallback`](@ref)を、`ode_euler`によって与えられた純粋な流れの`ODEProblem`に基づいて作成します。時間積分法`alg`と、`ode_euler`を解くためのキーワード引数を使用して積分器を作成します（詳細については[OrdinaryDiffEqのドキュメント](https://diffeq.sciml.ai/stable/)を参照してください）。音響ソルバーのCFL数`cfl_acoustics`と流れソルバーの`cfl_euler`で得られた最大ステップサイズの最小値を使用して、両方のソルバーのステップサイズを管理します。音響摂動方程式の平均値は`averaging_callback`から読み取られます（[`AveragingCallback`](@ref)を参照）。

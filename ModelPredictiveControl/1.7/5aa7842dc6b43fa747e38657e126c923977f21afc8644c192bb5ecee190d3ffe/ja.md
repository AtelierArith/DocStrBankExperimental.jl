```
sim!(
    mpc::PredictiveController, 
    N::Int,
    ry = mpc.estim.model.yop .+ 1, 
    d  = mpc.estim.model.dop,
    ru = mpc.estim.model.uop;
    <keyword arguments>
) -> res
```

`mpc` コントローラの閉ループシミュレーションを `N` ステップで実行し、出力セットポイントのバンプをデフォルトとします。

出力および操作された入力セットポイントは、それぞれ `ry` および `ru` で一定に保たれます。キーワード引数は [`sim!(::StateEstimator, ::Int)`](@ref) と同じです。

# 例

```jldoctest
julia> model = LinModel([tf(3, [30, 1]); tf(2, [5, 1])], 4);

julia> mpc = setconstraint!(LinMPC(model, Mwt=[0, 1], Nwt=[0.01], Hp=30), ymin=[0, -Inf]);

julia> res = sim!(mpc, 25, [0, 0], y_noise=[0.1], y_step=[-10, 0])
Simulation results of LinMPC with 25 time steps.
```

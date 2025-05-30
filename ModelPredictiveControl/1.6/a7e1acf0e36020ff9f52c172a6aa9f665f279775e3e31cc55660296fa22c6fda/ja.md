すべての予測コントローラーの抽象スーパタイプ。

---

```
(mpc::PredictiveController)(ry, d=[]; kwargs...) -> u
```

[`moveinput!`](@ref) のエイリアスとして呼び出し可能な `PredictiveController` オブジェクトを許可するファンクタ。

# 例

```jldoctest
julia> mpc = LinMPC(LinModel(tf(5, [2, 1]), 3), Nwt=[0], Hp=1000, Hc=1, direct=false);

julia> u = mpc([5]); round.(u, digits=3)
1-element Vector{Float64}:
 1.0
```

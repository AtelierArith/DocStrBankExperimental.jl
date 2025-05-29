```
steady_state_jac(rs::ReactionSystem; u0 = [])
```

ジャコビアン関数を作成します。これは、`steady_state_stability`への入力として使用できます。多くの安定性計算を効率的に実行する必要がある場合に便利です。

引数:     - `rs`: 安定性を計算したい反応系モデル。     - `u0 = []`: 保存則を持つ系の場合、保存量を計算するために`u`が必要です。

例:

```julia
# モデルを作成します。
rn = @reaction_network begin
    (p,d), 0 <--> X
end
p = [:p => 1.0, :d => 0.5]

# 定常状態のジャコビアンを作成します。
ss_jac = steady_state_jacobian(rn)

# （自明な）定常状態を見つけ、安定性を計算します。
steady_state = [2.0]
steady_state_stability(steady_state, rn, p; ss_jac)

注意:
    - 実際には、この関数は計算されたジャコビアンを持つ`ODEProblem`を返します。これは、`steady_state_stability`関数によって使用できるように設定されています。
```

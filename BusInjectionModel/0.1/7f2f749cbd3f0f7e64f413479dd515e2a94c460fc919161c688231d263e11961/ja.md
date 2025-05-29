```
build_bim_polar!(m::JuMP.AbstractModel, net::Network{SinglePhase}, ::Val{Unrelaxed})
```

単相の非緩和BIMを極座標電圧変数でモデル化するビルダー。詳細については、[Single Phase Bus Injection Model (Unrelaxed)](@ref)の数式を参照してください。

次の変数を追加します：

  * `m[:v_mag]` は `CommonOPF.busses(net)` のすべてのバスに対して
  * `m[:v_ang]` は `CommonOPF.busses(net)` のすべてのバスに対して
  * スラックバスの電力注入のための `m[:p0]` と `m[:q0]`
  * 任意のP-Vバスのための `m[:q_gen]` （`CommonOPF.Generator`を介して）

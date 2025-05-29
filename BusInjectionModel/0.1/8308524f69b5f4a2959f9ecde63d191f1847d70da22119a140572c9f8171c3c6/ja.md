```
build_bim_rectangular!(m::JuMP.AbstractModel, net::Network{MultiPhase}, ::Val{Unrelaxed})
```

多相、非緩和BIMのモデルビルダーで、矩形電圧変数を持ちます。詳細については、[Multi-Phase Bus Injection Model (Unrelaxed)](@ref)の数式を参照してください。

変数を追加します：

  * `m[:v]` は `CommonOPF.busses(net)` のすべてのバスに対して複素値を持ちます
  * `m[:s0]` は複素スラックバスの電力注入用です

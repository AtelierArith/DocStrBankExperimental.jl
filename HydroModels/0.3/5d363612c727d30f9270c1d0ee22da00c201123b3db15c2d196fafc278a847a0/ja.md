```
@hydroroute name begin ... end
```

`HydroRoute`オブジェクトの構築を簡素化するためのマクロ。

# 使用法

```julia
@hydroroute :my_route begin
    fluxes = [
        @hydroflux outflow ~ k * storage
    ]
    dfluxes = [
        @stateflux storage ~ inflow - outflow
    ]
    aggr_func = identity # または他の関数
end
```

指定された名前（`:my_route`）、フラックス、状態導関数（`dfluxes`）、および集約関数（`aggr_func`）を持つ`HydroRoute`を`begin...end`ブロック内で定義します。

# 引数

  * `name`: （オプション）ルート名のシンボル。
  * `block`: `fluxes`、`dfluxes`、および`aggr_func`の代入を含む`begin...end`ブロック。

# 戻り値

  * `HydroRoute`インスタンス。

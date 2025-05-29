```
evolve!(itoprocesses::Union{Dict{Symbol,ItoProcess{R}},Dict{Symbol,ItoProcess}}, stochastics::Union{Dict{Symbol,R},Dict{Symbol,Real}}, new_time::Real) where R<:Real
```

`ItoProcess`を前方に進化させます。これにより、時間（`t0`）と値が変更されます。

### 入力

  * `itoprocesses` - `ItoProcess`の`Dict`
  * `stochastic` - `ItoIntegral`からのサンプルの`Dict`。
  * `new_time` - 新しい時間。

### 戻り値

何も返しません。入力の`ItoProcess`を変更します。

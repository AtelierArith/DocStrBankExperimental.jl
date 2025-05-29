```
evolve_covar_and_ito_processes!(itoprocesses::Union{Dict{Symbol,ItoProcess{R}},Dict{Symbol,ItoProcess}}, covar::ForwardCovariance, new_time::Real; number_generator::NumberGenerator) where R<:Real
```

`ItoProcess`を前方に進化させます。

### 入力

  * `itoprocesses` - `ItoProcess`の`Dict`
  * `covar` - 共分散行列。
  * `new_time` - 新しい時間。
  * `number_generator` - 数値生成器

### 戻り値

  * 更新された`ItoProcess`
  * 共分散行列

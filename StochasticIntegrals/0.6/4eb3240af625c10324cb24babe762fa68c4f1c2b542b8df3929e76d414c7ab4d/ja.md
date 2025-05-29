```
evolve!(itoprocess::ItoProcess, stochastic::Real, new_time::Real)
```

`ItoProcess`を前方に進化させます。これにより、時間（`t0`）と`value`が変更されます。

### 入力

  * `itoprocess` - 進化させる`ItoProcess`。
  * `stochastic` - `ItoIntegral`からのサンプル。
  * `new_time` - 新しい時間。

### 返り値

何も返しません。入力の`ItoProcess`が変更されます。

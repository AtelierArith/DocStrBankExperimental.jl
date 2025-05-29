```
current_time(valp)
current_time(valp, i)
```

値プロバイダー `valp` の現在の時刻を返します。もし `is_timeseries(valp)` が [`Timeseries`](@ref) の場合、状態値が保存されている時刻のベクトルを返します。この場合、関数の二引数バージョンも、タイムステップ `i` の時刻を効率的に返すように実装できます。デフォルトでは、二引数メソッドは `current_time(p)[i]` を呼び出します。タイムシリーズは昇順にソートされていると仮定されています。

もし `i` が複数のインデックス（例えば、`Colon`、`AbstractArray{Int}`、`AbstractArray{Bool}`）で構成されている場合、効率のために特化したメソッドが定義されることがあります。デフォルトでは、`current_time(valp, ::Colon) = current_time(valp)` として、タイムシリーズのコピーを避けます。

デフォルトでは、単一引数バージョンは `valp isa AbstractVector` の場合、恒等関数として機能します。

参照: [`is_timeseries`](@ref) ```

```
set_param!(sim::Simulation, param::Symbol, value)
```

指定された `value` を `param` パラメータに割り当てます。この操作は `finish_init!` メソッドを呼び出す前にのみ許可されます。

`set_param!` のパイプ可能なバージョンも利用可能です。

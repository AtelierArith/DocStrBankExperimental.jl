```
set_solver_specific!(stats::GenericExecutionStats, field::Symbol, value)
```

`value`を`stats`内の`field`によって識別されるソルバー固有の値として登録し、それを信頼できるものとしてマークします。

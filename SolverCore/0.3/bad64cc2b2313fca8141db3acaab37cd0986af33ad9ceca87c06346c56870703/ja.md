```
broadcast_solver_specific!(stats::GenericExecutionStats, field::Symbol, value)
```

`value`を`stats`内の`field`によって特定されたソルバー固有の値としてブロードキャストし、それを信頼できるものとしてマークします。

```
activate!(arch::DistributedArchitecture; kwargs...)
```

指定されたDistributedArchitectureを子アーキテクチャに委任してアクティブにし、任意のキーワード引数を渡します。たとえば、優先度は`：normal`、`：low`、および`：high`の受け入れ可能な値で設定できます。

```
Unitary( U :: AbstractMatrix ) <: Operator{T}
```

ユニタリ行列は量子状態の物理的な進化を表します。コンストラクタ `Unitary(U)` は、提供された行列 `U` がユニタリでない場合に `DomainError` をスローします。

```
CPRPreconditioner(p = default_psolve(), s = ILUZeroPreconditioner(); strategy = :quasi_impes, weight_scaling = :unit, update_frequency = 1, update_interval = :iteration, partial_update = true)
```

制約付き圧力残差 (CPR) 前処理器を構築します。

デフォルトでは、これはAMG-BILU(0)バージョンです（圧力の代数的多重格子法、グローバルシステムのブロック-ILU(0)）。

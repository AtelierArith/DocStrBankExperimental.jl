```
XPRS_SERIALIZEPREINTSOL
```

`SERIALIZEPREINTSOL`を1に設定すると、並列MIPソルブ中に`preintsol`コールバックが常に決定論的な順序で発火することが保証されます。（整数）

これは、制御DETERMINISTICが`1`に設定されている場合にのみ適用されます。

デフォルト値: `0`

値: 0 : `preintsol`コールバックは異なるスレッドから非同期に発火します。 1 : `preintsol`コールバックは決定論的な順序で発火します。

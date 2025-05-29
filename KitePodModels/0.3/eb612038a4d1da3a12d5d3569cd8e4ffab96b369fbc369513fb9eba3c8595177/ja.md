```
init_kcu!(kcu::KCU, set::KiteUtils.Settings)
```

カイトコントロールユニット（KCU）のモデルを初期化します。デパワーの実際の値と設定値は set.depower_offset * 0.01 に初期化され、ステアリングの実際の値と設定値はゼロに初期化されます。

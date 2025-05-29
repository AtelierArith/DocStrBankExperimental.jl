```
requiresWritingCheckpoint()::Bool
```

ソルバーがチェックポイントを書き込む必要があるかどうかを確認します。チェックポイントの書き込みが必要な場合、preCICEは進行を拒否しますが、このメソッドはadvance()の前に呼び出されません。

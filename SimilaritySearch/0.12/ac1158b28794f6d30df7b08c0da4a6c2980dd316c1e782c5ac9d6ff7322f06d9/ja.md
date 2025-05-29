```
abstract type Callback end
```

挿入の数に応じてコールバックをトリガーするための抽象型。SearchGraphは`callbacks`（シンボルとコールバックオブジェクトを関連付ける辞書）にコールバックを格納します。SearchGraphオブジェクトは、`callback_logbase`と`callback_starting`を使用してコールバックが発火するタイミングを制御します。

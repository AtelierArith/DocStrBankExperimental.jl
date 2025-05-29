```
AbstractUncertainIndexValueDataset
```

不確実な値（`UncertainValue` インスタンス）のデータセットで、インデックス（時間、深さなど）も不確実な値（`UncertainValue` インスタンス）です。

具体的な型は、最低限以下のフィールドを実装する必要があります：

  * **`indices::UncertainDataset`**: データセットの（不確実な）インデックス。
  * **`values::UncertainDataset`**: データセットの（不確実な）値。

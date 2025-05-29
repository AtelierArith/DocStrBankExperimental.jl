```
setstyle!(n::Node, s::Style; reconcile=true)
```

ノード `n` に関連付けられたスタイルを `s` に設定します。`reconcile` が真の場合、内部的一貫性のためにフィールドを適切に修正します。

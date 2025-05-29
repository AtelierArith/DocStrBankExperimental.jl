```
struct NewSSAValue
```

`NewSSAValue`はIncrementalCompactの文脈で発生します。その意味は出現する場所によって異なります：

1. すでに圧縮されたノードでは、 i. 正の`id`を持つ`NewSSAValue`は通常のSSAValueと同じ意味を持ちます。 ii. 負の`id`を持つ`NewSSAValue`は、圧縮後の`new_node`ノードを指します。
2. 非圧縮ノードでは、 i. 正の`id`を持つ`NewSSAValue`は、すでに圧縮された命令のインデックスを指します。 ii. 負の`id`を持つ`NewSSAValue`は、圧縮されたノードと同じ意味を持ちます。

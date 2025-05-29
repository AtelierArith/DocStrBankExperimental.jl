```
deletebranch!(model::Model, branch::Branch)
```

`model`の分岐から`branch`を削除します。

```
deletebranch!(model::Model, srcnode::Node, dstnode::Node)
```

`model`の`srcnode`と`dstnode`の間の分岐を削除します。

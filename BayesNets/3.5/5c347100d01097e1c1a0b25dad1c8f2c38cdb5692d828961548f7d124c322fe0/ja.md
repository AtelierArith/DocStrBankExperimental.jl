```
delete!(bn::BayesNets, target::NodeName)
```

cpdを削除すると、頂点のインデックスが変更されます。特に、i番目のcpdを削除すると、iとnが入れ替わり、その後nが削除されます。

```
Q = get_qm(pedlist)
Q = get_qm(T, pedlist)
```

未知の親グループ（UPG）と個体を関連付けるQ行列を計算します。これはQuaas（1988）によって提案されました。系譜リスト`pedlist`には、実際の動物の最大IDよりも大きいUPGコードが含まれている必要があります。`Q`の型は`T`（デフォルトではFloat64）です。

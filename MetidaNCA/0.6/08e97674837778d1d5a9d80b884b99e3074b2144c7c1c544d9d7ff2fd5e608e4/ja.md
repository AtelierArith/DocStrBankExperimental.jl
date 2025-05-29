```
vpcplot(data::DataSet{T}; timef = identity, meanf = mean, intf = x->qf(x, 0.05), kwargs...) where T <: Union{PKSubject, PDSubject}
```

各時間点での平均と0.05 - 0.95の分位数範囲をプロットします。

`timef` - 時間点を変換するために使用できる関数。

`meanf` - デフォルトは`mean`で、他の統計関数も使用できます。

`intf` - 各時間点の上限と下限を計算するための関数。デフォルトでは次のように使用されます：

```
qf(x, alpha) = (quantile(x, alpha), quantile(x, 1-alpha))
```

他のキーワードは`plot`関数に渡されます。

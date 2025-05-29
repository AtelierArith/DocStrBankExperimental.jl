```
LinkedPropertyListener(fn, target::RecoPlan, targetProp, source::RecoPlan, sourceProp)
```

`RecoPlans`の2つのプロパティを接続します。`source.sourceProp`が変更されるたびに`target.targetProp`を`fn(source.sourceProp)`に設定し、リスナーの外部で`target.targetProp`が変更されていない場合に限ります。

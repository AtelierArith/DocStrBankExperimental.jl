```
SimpleKRatioOptimizer(overvoltage, favor::Vector{CharXRay} = CharXRay[], minOvervoltage=1.2)
```

シンプルなオプティマイザーを実装します。これは、最初にシェル、次にオーバーボルテージ、最後に明るさに基づいています。要素の最適なラインセットを選択すると、それは変更されません。特定のラインの選択を強制するには、`favor`にファミリー内で最も明るいものを含めることができます。オーバーボルテージが`minOvervoltage`未満のラインは、利用可能として考慮されません。

```
ComposedStopCondition(stop_conditions...; reducer = any)
```

`stop_conditions`の結果は`reducer`によって縮約されます。デフォルトの`reducer`は`any`関数であり、これは`stop_conditions...`のいずれかが真であれば条件が真であることを意味します。ブール値を返す任意の関数に置き換えることができます。例えば、`reducer = x->sum(x) >= 2`は、条件のうち少なくとも2つが真であることを要求します。

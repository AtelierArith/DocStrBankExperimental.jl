```
parentproperty(plan::RecoPlan)
```

`plan`の親におけるプロパティ名を返します。すなわち、`getproperty(parent(plan), parentproperty(plan)) === plan`が成り立ちます。`plan`に親がない場合は`nothing`を返します。

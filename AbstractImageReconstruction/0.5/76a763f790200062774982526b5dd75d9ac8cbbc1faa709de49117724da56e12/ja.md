```
parentproperties(plan::RecoPlan)
```

`plan`の親のプロパティ名のベクターを返します。すなわち、`getproperty(parent(plan), last(parentproperties(plan))) === plan`が成り立ちます。`plan`に親がない場合は空のベクターを返します。

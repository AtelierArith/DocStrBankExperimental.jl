```julia
struct Always <: ValueConstraints.Interface.AbstractConstraint
```

どの`value`がそれに対して検証されても有効な制約を表します。

制約の検証が簡単ではない場合に、テストなどでコードをショートサーキットするのに役立ちます。

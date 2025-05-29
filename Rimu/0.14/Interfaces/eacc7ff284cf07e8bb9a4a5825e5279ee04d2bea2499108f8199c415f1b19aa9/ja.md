```
deposit!(w::AbstractDVec, add, val, parent::Pair)
```

`val`を`w`のアドレス`add`に追加し、適用可能な場合はイニシエーターのルールを考慮します。`parent`には、ペア`add => val`が作成された`address => value`ペアが含まれています。 [`InitiatorDVec`](@ref Main.DictVectors.InitiatorDVec)はこれをインターセプトし、自身の機能を追加することができます。

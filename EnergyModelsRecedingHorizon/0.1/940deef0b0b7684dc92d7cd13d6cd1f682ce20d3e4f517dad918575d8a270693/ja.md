```
struct ElementValue{T<:Union{TimeProfile, Real}}
```

`ElementValue`は、与えられた[`AbstractElement`](@extref EnergyModelsBase.AbstractElement)のインスタンスを、割り当てられた値と共に表します。これは、`AbstractElement`がキー値として使用される辞書を置き換え、`AbstractElement`をリセットできるようにします。

## フィールド

  * **`element::N`** は要素のインスタンスです。
  * **`value::T`** は使用される値です。

```
AndersonAccelerator{T, BT, MT, RE} <: AbstractAccelerator
```

Anderson加速を実装するアクセラレータオブジェクト。パラメータは次の通り：

  * T: AbstractFloat、浮動小数点型
  * BT: Broyden型、すなわちType1またはType2
  * MT: AbstractMemory、メモリバッファの扱い方
  * RE: AbstractRegularizer

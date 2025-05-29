```
setTransverseMass!(lv,value)
```

`LorentzVectorLike`の横方向の質量を指定された`value`に設定します。

!!! note
    `setTransverseMass!`で設定された`value`は、[`getTransverseMass`](@ref)によって返されます。横方向の質量は`getTransverseMass`の呼び出し時に計算されるため、セッター`setTransverseMass!`は指定された`LorentzVectorLike`のいくつかの成分を変更します。


```
setTransverseMomentum!(lv,value)
```

`LorentzVectorLike`の横運動量を指定された`value`に設定します。

!!! note
    `setTransverseMomentum!`で設定された`value`は、[`getTransverseMomentum`](@ref)によって返されます。横運動量は`getTransverseMomentum`の呼び出し時に計算されるため、セッター`setTransverseMomentum!`は指定された`LorentzVectorLike`のいくつかの成分を変更します。


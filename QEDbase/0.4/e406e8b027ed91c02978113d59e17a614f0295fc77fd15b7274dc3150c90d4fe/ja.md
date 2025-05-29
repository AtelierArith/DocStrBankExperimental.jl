```
setRho!(lv,value)
```

`LorentzVectorLike`の大きさを指定された`value`に設定します。

!!! note
    `setRho!`で設定された`value`は、その後[`getRho`](@ref)によって返されます。大きさは`getRho`の呼び出し時に計算されるため、セッター`setRho!`は指定された`LorentzVectorLike`のいくつかのコンポーネントを変更します。


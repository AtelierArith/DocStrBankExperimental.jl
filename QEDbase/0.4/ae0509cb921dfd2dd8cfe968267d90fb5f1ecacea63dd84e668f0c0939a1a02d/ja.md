```
setTheta!(lv,value)
```

`LorentzVectorLike`のシータ角を指定された`value`に設定します。

!!! note
    `setTheta!`で設定された`value`は、[`getTheta`](@ref)によって返されます。シータ角は`getTheta`の呼び出し時に計算されるため、セッター`setTheta!`は指定された`LorentzVectorLike`のいくつかのコンポーネントを変更します。


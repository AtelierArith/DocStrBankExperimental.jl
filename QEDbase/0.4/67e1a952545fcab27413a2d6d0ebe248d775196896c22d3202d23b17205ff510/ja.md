```
setCosTheta!(lv,value)
```

`LorentzVectorLike`のθ角のコサインを指定された`value`に設定します。

!!! note
    `setCosTheta!`で設定された`value`は、[`getCosTheta`](@ref)によって返されます。θ角のコサインは`getCosTheta`の呼び出し時に計算されるため、セッター`setCosTheta!`は指定された`LorentzVectorLike`のいくつかのコンポーネントを変更します。


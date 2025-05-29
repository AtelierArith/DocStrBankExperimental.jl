```
setRapidity!(lv,value)
```

`LorentzVectorLike`のラピディティを指定された`value`に設定します。

!!! note
    `setRapidity!`で設定された`value`は、その後[`getRapidity`](@ref)によって返されます。ラピディティは`setRapidity`の呼び出し時に計算されるため、セッター`setRapidity!`は指定された`LorentzVectorLike`のいくつかのコンポーネントを変更します。


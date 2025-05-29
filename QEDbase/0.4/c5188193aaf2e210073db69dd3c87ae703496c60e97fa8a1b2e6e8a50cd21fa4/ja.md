```
setMinus!(lv,value)
```

`LorentzVectorLike`のマイナス成分を指定された`value`に設定します。

!!! note
    `setMinus!`で設定された`value`は、その後[`getMinus`](@ref)によって返されます。マイナス成分は`getMinus`の呼び出し時に計算されるため、セッター`setMinus!`は指定された`LorentzVectorLike`のいくつかの成分を変更します。


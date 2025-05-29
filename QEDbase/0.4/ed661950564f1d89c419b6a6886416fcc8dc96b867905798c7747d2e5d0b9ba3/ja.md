```
setPhi!(lv,value)
```

`LorentzVectorLike`のphi角を指定された`value`に設定します。

!!! note
    `setPhi!`で設定された`value`は、[`getPhi`](@ref)によって返されます。phi角は`getPhi`の呼び出し時に計算されるため、セッター`setPhi!`は指定された`LorentzVectorLike`のいくつかのコンポーネントを変更します。


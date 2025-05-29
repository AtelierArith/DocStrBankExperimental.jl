```
transfer_dem_free!(source::Balance, destination::Balance, amount::Real)
```

デマレージフリーのバッファの一部または全部を、あるバランスから別のバランスに転送します。利用可能なデマレージフリーのバッファ以上は転送できません。

  * source::Balance - デマレージフリーの金額が引き出されるバランス。
  * destination::Balance - デマレージフリーのバッファが転送されるバランス。
  * amount::Real - 転送される金額。
  * return - 取引が成功したかどうか。

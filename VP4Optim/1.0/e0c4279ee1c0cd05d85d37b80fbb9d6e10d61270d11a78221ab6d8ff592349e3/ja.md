```
modpar(mp::ModPar{T}; kwargs...) where {T <: Model}
```

## 引数

  * `mp::ModPar{T}`: 変更される既存のモデルパラメータ。
  * `kwargs`: 任意の数のキーワード引数。

## 戻り値

  * 型 `<: ModPar{T}` のインスタンス。

## 備考

  * 引数 `mp` は *変更されません*。

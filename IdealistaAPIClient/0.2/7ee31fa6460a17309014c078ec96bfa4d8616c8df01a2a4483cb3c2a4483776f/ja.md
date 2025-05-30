```
valid_fields(T::Type; indent::Int=0)
```

型 T のフィールド名を印刷します

渡された型のフィールド名を標準出力に印刷します

# キーワード引数

  * indent: インデントのタブ数

# 例

```julia
julia>valid_fields(Garages)
bankOffer
automaticDoor
motorcycleParking
security

```

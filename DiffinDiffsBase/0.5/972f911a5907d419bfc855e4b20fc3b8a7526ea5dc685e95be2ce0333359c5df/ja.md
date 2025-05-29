```
ScaledArray(x::AbstractArray, start, step[, stop]; reftype=Int32, usepool=true)
ScaledArray(x::AbstractArray, step; reftype=Int32, start, stop, usepool=true)
```

`x`から`step`サイズを指定して`ScaledArray`を構築します。`start`または`stop`が指定されていない場合、`x`の極値に基づいて選択されます。

# キーワード

  * `reftype::Type=Int32`: フィールド`refs`の要素タイプ。
  * `usepool::Bool=true`: `DataAPI.refpool`に基づいて`x`の極値を見つけます。

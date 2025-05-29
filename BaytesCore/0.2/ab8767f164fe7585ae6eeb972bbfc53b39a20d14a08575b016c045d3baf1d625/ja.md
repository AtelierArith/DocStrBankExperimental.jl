```julia
mutable struct ValueHolder{T<:Real}
```

不変構造体に格納および更新できる単一のスカラー値を保持するための可変構造体です。

# フィールド

  * `current::Real`: スカラー値

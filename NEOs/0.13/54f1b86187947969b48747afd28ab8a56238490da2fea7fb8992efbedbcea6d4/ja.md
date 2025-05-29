```
jplcompare(des::String, sol::NEOSolution{T, U}) where {T <: Real, U <: Number}
```

`abs.(sol() - R) ./ sigmas(sol)`を返します。ここで、`R`は`sol`の初期エポックにおけるオブジェクト`des`のJPLの状態ベクトルです。

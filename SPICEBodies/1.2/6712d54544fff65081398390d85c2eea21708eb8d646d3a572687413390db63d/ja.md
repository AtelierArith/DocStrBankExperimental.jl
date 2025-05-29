与えられたエポックに対して、観測者によって定義された `wrt` に対する天体の状態ベクトル `[x, y, z, ẋ, ẏ, ż]` (KM,KM/s) を返します。基礎となる実装に関する詳細は `spkez` を参照してください。`dimension` キーワード引数を使用して、完全な状態ベクトル、`Val(:position)`、または `Val(:velocity)` のいずれを取得したいかを指定します。

```julia
body(epoch; frame = "J2000", aberration = "none", wrt = naifcode("ssb"), dimension = Val(:all))
```

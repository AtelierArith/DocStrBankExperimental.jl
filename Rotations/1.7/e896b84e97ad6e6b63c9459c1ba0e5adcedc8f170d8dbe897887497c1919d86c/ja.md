```
(*)(q::QuatRotation, w::QuatRotation)
```

クォータニオン合成

次のものと同等です

```julia
lmult(q) * SVector(w)
rmult(w) * SVector(q)
```

出力マッピングを `w` のマッピングに等しく設定します

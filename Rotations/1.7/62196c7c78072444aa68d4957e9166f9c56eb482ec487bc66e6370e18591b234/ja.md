```
(*)(q::QuatRotation, r::StaticVector)
```

ベクトルを回転させる

`hmat()' lmult(q) * rmult(q)' hmat() * r` と同等です。

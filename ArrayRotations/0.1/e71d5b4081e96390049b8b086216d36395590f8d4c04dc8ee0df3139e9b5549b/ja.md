```
rotate!(::AuxRotation, A::AbstractVector, tailpos::Integer)
```

`A`を`tailpos`で回転させ、最大で`n / 2`の追加メモリと3n/2のコピー書き込み操作を使用します。

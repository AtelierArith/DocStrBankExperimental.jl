```
rotate!(::RevRotation, A::AbstractVector, tailpos::Integer)
```

`A`を`tailpos`で回転させますが、$O(1)$の追加メモリを使用し、いくつかの2nコピー書き込み操作（トリプルリバース）を使用します。

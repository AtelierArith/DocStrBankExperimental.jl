```
rotate!(bridge::BridgeRotation, A::AbstractVector, tailpos::Integer)
```

`A`を`tailpos`で回転させます。追加のメモリは少量で、Aの3分の1以下およびn+n/3のコピー書き込み操作以下です。

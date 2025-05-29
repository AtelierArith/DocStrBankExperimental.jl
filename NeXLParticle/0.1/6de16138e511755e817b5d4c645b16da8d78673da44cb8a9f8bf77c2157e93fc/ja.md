```
separate(b::Blob, concavity = 0.42, withinterior = true)::Vector{Blob}
```

bを周囲の凹面を探して多くのBlob(s)に分割し、それらを短い線で結びます。

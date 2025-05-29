```
fastgensphere(N::Int64, d::Int64; par::Bool=true)
```

次元 d の単位球上で長さ N の lds を生成するより高速な方法です。

`gensphere()` に似ています。この関数ははるかに高速で、並列処理をサポートしていますが、d が大きいと退化する可能性があります。

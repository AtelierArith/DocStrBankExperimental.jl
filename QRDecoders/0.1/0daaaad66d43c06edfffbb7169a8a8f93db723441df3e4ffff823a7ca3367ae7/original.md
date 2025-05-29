```
qrdecode(mat::AbstractMatrix
        ; noerror::Bool=false
        , preferutf8::Bool=true
        , alg::ReedSolomonAlgorithm=Euclidean()
        )::QRInfo
```

QR code decoder.

If `noerror` is `true`, the decoder will raise an Exception(ReedSolomonError/InfoError) when the QR code `mat` needs error correction.

If `preferutf8` is `true`, the decoder will try to decode the message by `UTF8` mode when dealing with `Byte` mode.

The error correction algorithm is specified by the variable `alg`(default: `Euclidean`).

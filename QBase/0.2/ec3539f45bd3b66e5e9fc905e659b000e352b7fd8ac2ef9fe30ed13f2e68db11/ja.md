```
PVM( Π :: Vector{Vector{T}}; atol=ATOL :: Float64 ) <: Measurement{T}
```

射影値測度の具体的な型です。射影は直交正規基底ベクトルの集合として表されます。

`Π` が直交正規基底を含まない場合、`DomainError` がスローされます。

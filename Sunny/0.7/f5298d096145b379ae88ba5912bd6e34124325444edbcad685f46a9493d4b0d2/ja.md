```
dmvec(D)
```

Dzyaloshinskii-Moriya擬ベクトルの反対称行列表現、

```
  [  0    D[3] -D[2]
   -D[3]   0    D[1]
    D[2] -D[1]   0  ]
```

構成により、`Si'*dmvec(D)*Sj ≈ D⋅(Si×Sj)` は任意の双極子 `Si` と `Sj` に対して成り立ちます。このヘルパー関数は [`set_exchange!`](@ref) と一緒に使用することを意図しています。

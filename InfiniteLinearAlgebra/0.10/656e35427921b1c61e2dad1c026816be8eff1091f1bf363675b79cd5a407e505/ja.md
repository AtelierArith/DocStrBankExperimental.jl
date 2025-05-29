```
BidiagonalConjugation(U, X, V, uplo)
```

行列積 `inv(U)XV` の投影を効率的に計算し、バイ対角行列にします。`uplo` 引数は、投影が上部（`uplo = 'U'`）か下部（`uplo = 'L'`）のバイ対角であるかを指定します。

計算結果は、対角および非対角ベクトルが遅延計算される `Bidiagonal` 行列として返されます。

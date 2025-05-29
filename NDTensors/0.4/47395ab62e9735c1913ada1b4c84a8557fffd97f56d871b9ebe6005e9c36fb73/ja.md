```
random_unitary(n::Int,m::Int)::Matrix{ComplexF64}
random_unitary(::Type{ElT},n::Int,m::Int)::Matrix{ElT}
```

次の条件を満たす次元 (n,m) のランダム行列 U を返します。n >= m の場合、U'*U は単位行列になります。また、m > n の場合、U*U' は単位行列になります。オプションで、最初の引数に数値型を渡すことで、その型の行列を取得できます。

サンプリングは https://arxiv.org/abs/math-ph/0609050 に基づいており、`n==m` の場合、ユニタリ行列は Haar 測度に従ってサンプリングされます。

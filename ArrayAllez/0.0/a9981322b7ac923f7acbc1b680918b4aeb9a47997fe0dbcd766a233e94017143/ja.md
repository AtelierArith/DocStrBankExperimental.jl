```
scale!(A, b::Number) ≈ A .* b
scale!(M, v::Vector) ≈ A .* v       # M::Matrix
scale!(M, r::Adjoint) ≈ A .* r      # r::RowVector / Transpose etc.
scale!(A, B) ≈ A .* B               # A,B same ndims
```

定数によるインプレーススケーリング、または（行列の場合）行ベクトルまたは列ベクトルによるスケーリング。これらのそれぞれに対して、非破壊的だがおそらく加速された `scale_(A, ...)` と、単純なブロードキャスティングの `scale0(A, ...)` もあります。

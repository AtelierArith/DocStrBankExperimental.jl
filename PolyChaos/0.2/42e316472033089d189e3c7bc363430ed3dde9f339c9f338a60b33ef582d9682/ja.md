```
rm_jacobi(N::Int,a::Real,b::Real)
rm_jacobi(N::Int,a::Real)
rm_jacobi(N::Int)
```

モニックジャコビ多項式のための `N` 再帰係数を生成します。これらは $(-1,1)$ 上で $w(t) = (1-t)^a (1+t)^b$ に対して直交します。

呼び出し `rm_jacobi(N,a)` は `rm_jacobi(N,a,a)` と同じであり、`rm_jacobi(N)` は `rm_jacobi(N,0,0)` と同じです。

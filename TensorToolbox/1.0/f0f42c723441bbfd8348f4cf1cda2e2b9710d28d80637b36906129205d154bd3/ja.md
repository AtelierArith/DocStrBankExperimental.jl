```
TTtv(X::TTtensor,u::VectorCell,mode::Int)
TTtv(X::TTtensor,U::AbstractMatrix{<:Number},mode::Int)
TTtv(X::CoreCell,u::VectorCell)
TTtv(X::CoreCell,U::AbstractMatrix{<:Number})
```

TTテンソルとベクトルの積。N=ndims(X) および n=[mode,mode+1,...,N] の場合、TTテンソルの n 番目のコアをベクトル u[N-n+1] と収束させます。入力が行列の場合、ベクトル u はその列になります。コアのサブセットで呼び出すと、与えられたすべてのコアをベクトルに収束させます。

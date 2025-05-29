```
KernelMatrix{Tf,Tx,Ty,T} <:: AbstractKernelMatrix{T}
```

2つの要素のセットに作用するカーネル関数を表す一般的なカーネル行列。`K`が`KernelMatrix`である場合、`K[i,j] = f(X[i],Y[j])` であり、ここで `f::Tf=kernel(K)`、`X::Tx=rowelements(K)`、`Y::Ty=colelements(K)`です。

# 例

```julia
X = rand(SVector{2,Float64},2)
Y = rand(SVector{2,Float64},2)
K = KernelMatrix(X,Y) do x,y
    sum(x+y)
end
```

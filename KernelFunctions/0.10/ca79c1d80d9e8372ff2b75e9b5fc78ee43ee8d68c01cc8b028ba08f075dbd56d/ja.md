```
KernelProduct <: Kernel
```

カーネルの積を作成します。オーバーロードされた演算子 `*` を使用することもできます。

`KernelProduct` を作成する方法はいくつかあります：

`KernelProduct` を指定する最も簡単な方法は、オーバーロードされた `*` 演算子を使用することです。これは、カーネルをコンストラクタの引数として指定して `KernelProduct` を作成することと同等です。  

```jldoctest kernelprod
julia> k1 = SqExponentialKernel(); k2 = LinearKernel(); X = rand(5);

julia> (k = k1 * k2) == KernelProduct(k1, k2)
true

julia> kernelmatrix(k1 * k2, X) == kernelmatrix(k1, X) .* kernelmatrix(k2, X)
true

julia> kernelmatrix(k, X) == kernelmatrix(k1 * k2, X)
true
```

カーネルを掛け算するために `Tuple` または `Vector` を提供することで `KernelProduct` を指定することもできます。コンポーネントが少ない場合は `Tuple` を使用し、多くのコンポーネントを扱う場合は `Vector` を使用することをお勧めします。

```jldoctest kernelprod
julia> KernelProduct((k1, k2)) == k1 * k2
true

julia> KernelProduct([k1, k2]) == KernelProduct((k1, k2)) == k1 * k2
true
```

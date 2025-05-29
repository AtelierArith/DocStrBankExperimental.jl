```
KernelSum <: Kernel
```

カーネルの合計を作成します。演算子 `+` を使用することもできます。

`KernelSum` を作成する方法はいくつかあります：

`KernelSum` を指定する最も簡単な方法は、オーバーロードされた `+` 演算子を使用することです。これは、カーネルをコンストラクタの引数として指定することによって `KernelSum` を作成することと同等です。

```jldoctest kernelsum
julia> k1 = SqExponentialKernel(); k2 = LinearKernel(); X = rand(5);

julia> (k = k1 + k2) == KernelSum(k1, k2)
true

julia> kernelmatrix(k1 + k2, X) == kernelmatrix(k1, X) .+ kernelmatrix(k2, X)
true

julia> kernelmatrix(k, X) == kernelmatrix(k1 + k2, X)
true
```

カーネルの合計を指定するために、カーネルの `Tuple` または `Vector` を提供することもできます。コンポーネントが少ない場合は `Tuple` を使用し、多くのコンポーネントを扱う場合は `Vector` を使用することをお勧めします。

```jldoctest kernelsum
julia> KernelSum((k1, k2)) == k1 + k2
true

julia> KernelSum([k1, k2]) == KernelSum((k1, k2)) == k1 + k2
true
```

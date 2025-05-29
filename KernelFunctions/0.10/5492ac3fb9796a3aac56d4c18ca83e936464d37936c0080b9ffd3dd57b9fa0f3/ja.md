```
KernelTensorProduct
```

カーネルのテンソル積。

# 定義

入力 $x = (x_1, \ldots, x_n)$ と $x' = (x'_1, \ldots, x'_n)$ に対して、カーネル $k_1, \ldots, k_n$ のテンソル積は次のように定義されます。

$$
k(x, x'; k_1, \ldots, k_n) = \Big(\bigotimes_{i=1}^n k_i\Big)(x, x') = \prod_{i=1}^n k_i(x_i, x'_i).
$$

# 構築

`KernelTensorProduct` を指定する最も簡単な方法は、オーバーロードされた `tensor` 演算子またはそのエイリアス `⊗` を使用することです（`\otimes<tab>` と入力できます）。

```jldoctest tensorproduct
julia> k1 = SqExponentialKernel(); k2 = LinearKernel(); X = rand(5, 2);

julia> kernelmatrix(k1 ⊗ k2, RowVecs(X)) == kernelmatrix(k1, X[:, 1]) .* kernelmatrix(k2, X[:, 2])
true
```

カーネルを個別の引数または `Tuple` や `Vector` のような反復可能なデータ構造として提供することでも `KernelTensorProduct` を指定できます。タプルまたは個別の引数を使用すると、`KernelTensorProduct` が具体的に型付けされることが保証されますが、カーネルの数が多い場合はコンパイル時間が長くなる可能性があります。

```jldoctest tensorproduct
julia> KernelTensorProduct(k1, k2) == k1 ⊗ k2
true

julia> KernelTensorProduct((k1, k2)) == k1 ⊗ k2
true

julia> KernelTensorProduct([k1, k2]) == k1 ⊗ k2
true
```

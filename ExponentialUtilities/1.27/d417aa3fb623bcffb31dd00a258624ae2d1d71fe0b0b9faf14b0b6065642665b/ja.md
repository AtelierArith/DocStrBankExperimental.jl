```
E=exponential!(A,[method [cache]])
```

指定された`method`で行列指数関数を計算します。`A`の内容は変更され、より少ないアロケーションが可能になります。`method`パラメータは、実装と実装パラメータを指定します。例えば、[`ExpMethodNative`](@ref)、[`ExpMethodDiagonalization`](@ref)、[`ExpMethodGeneric`](@ref)、[`ExpMethodHigham2005`](@ref)などです。必要なメモリは事前に割り当てられ、`cache`パラメータで提供されるため、`exponential!`を何度も呼び出す際にメモリを再利用できます。事前割り当ては、コマンド[`alloc_mem`](@ref)を使用して行います：`cache=alloc_mem(A,method)`。`A`はスパース行列型であってはならず、exp(A)は密である可能性が高いためです。

例

```julia-repl
julia> A = randn(50, 50);

julia> B = A * 2;

julia> method = ExpMethodHigham2005();

julia> cache = ExponentialUtilities.alloc_mem(A, method); # ここで主な割り当てが行われます

julia> E1 = exponential!(A, method, cache) # ここでの割り当ては非常に少ないです

julia> E2 = exponential!(B, method, cache) # ここでの割り当ては非常に少ないです

```

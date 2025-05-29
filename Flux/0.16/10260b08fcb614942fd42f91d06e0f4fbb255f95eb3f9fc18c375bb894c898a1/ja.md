```
Maxout(layers...)
Maxout(f, n_alts)
```

これは内部層の数を含み、それぞれが同じ入力を受け取ります。その出力は内部層の出力の要素ごとの最大値です。

層を個別に定義する代わりに、それらを構築するゼロ引数関数と、構築する数を提供することができます。

線形密な層に対するMaxoutは、普遍近似定理を満たします。Goodfellow, Warde-Farley, Mirza, Courville & Bengioの「Maxout Networks」 [https://arxiv.org/abs/1302.4389](https://arxiv.org/abs/1302.4389) を参照してください。

他の演算子と一緒に削減するために [`Parallel`](@ref) も参照してください。

# 例

```jldoctest
julia> m = Maxout(x -> abs2.(x), x -> x .* 3);

julia> m([-2 -1 0 1 2])
1×5 Matrix{Int64}:
 4  1  0  3  6

julia> m3 = Maxout(() -> Dense(5 => 7, tanh), 3)
Maxout(
  Dense(5 => 7, tanh),                  # 42 parameters
  Dense(5 => 7, tanh),                  # 42 parameters
  Dense(5 => 7, tanh),                  # 42 parameters
)                   # Total: 6 arrays, 126 parameters, 816 bytes.

julia> Flux.outputsize(m3, (5, 11))
(7, 11)
```

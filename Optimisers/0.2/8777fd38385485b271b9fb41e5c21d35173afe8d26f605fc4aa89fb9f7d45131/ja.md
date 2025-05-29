```
destructure(model) -> vector, reconstructor
```

モデル内のすべての [`trainable`](@ref)、[`isnumeric`](@ref) パラメータをベクトルにコピーし、この変換を逆にする関数も返します。微分可能です。

# 例

```jldoctest
julia> v, re = destructure((x=[1.0, 2.0], y=(sin, [3.0 + 4.0im])))
(ComplexF64[1.0 + 0.0im, 2.0 + 0.0im, 3.0 + 4.0im], Restructure(NamedTuple, ..., 3))

julia> re([3, 5, 7+11im])
(x = [3.0, 5.0], y = (sin, ComplexF64[7.0 + 11.0im]))
```

`model` にさまざまな数値型が含まれている場合、それらは `vector` にするために昇格され、通常は `Restructure` によって復元されます。このような復元は `ChainRulesCore.ProjectTo` のルールに従い、浮動小数点精度を復元しますが、`ForwardDiff.Dual` のようなよりエキゾチックな数値も許可します。

`model` にGPU配列のみが含まれている場合、`vector` もGPU上に存在します。現在、GPUと通常のCPU配列の混合は未定義の動作です。

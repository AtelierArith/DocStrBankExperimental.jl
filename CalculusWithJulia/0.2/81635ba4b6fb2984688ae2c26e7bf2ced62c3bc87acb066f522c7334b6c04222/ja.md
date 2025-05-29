sign_chart(f, a, b; atol=1e-4)

`f`の`(a,b)`における符号チャートを作成します。識別されたゼロまたは垂直漸近線と対応する符号変化を持つ名前付きタプルのコレクションを返します。許容誤差は、数値的に見つかった値を曖昧にしないために使用されます。

# 例

```
julia> sign_chart(x -> (x-1/2)/(x*(1-x)), 0, 1)
3-element Vector{NamedTuple{(:zero_oo_NaN, :sign_change)}}:
 (zero_oo_NaN = 0.0, sign_change = an endpoint)
 (zero_oo_NaN = 0.5, sign_change = - to +)
 (zero_oo_NaN = 1.0, sign_change = an endpoint)
```

!!! note "警告"
    これは`find_zeros`を使用して`f`および`x -> 1/f(x)`のゼロを見つけます。`find_zeros`関数はヒューリスティックであり、解を見逃す可能性があります。


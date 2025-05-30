```
frule([::RuleConfig,] (Δf, Δx...), f, x...)
```

`f(x...)`の出力を`Ω`として表現し、タプルを返します:

```julia
(Ω, ΔΩ)
```

2番目の返り値は出力に関する接線です。

`frule((Δf, Δx...), f, x...)`に一致するメソッドが定義されていない場合は、`nothing`を返します。

例:

単項入力、単項出力スカラー関数:

```jldoctest frule
julia> dself = NoTangent();

julia> x = rand()
0.8236475079774124

julia> sinx, Δsinx = frule((dself, 1), sin, x)
(0.7336293678134624, 0.6795498147167869)

julia> sinx == sin(x)
true

julia> Δsinx == cos(x)
true
```

単項入力、二項出力スカラー関数:

```jldoctest frule
julia> sincosx, Δsincosx = frule((dself, 1), sincos, x);

julia> sincosx == sincos(x)
true

julia> Δsincosx[1] == cos(x)
true

julia> Δsincosx[2] == -sin(x)
true
```

技術的に言えば、juliaには複数出力関数は存在せず、単一の出力を返す関数があり、それは`Tuple`のように反復可能です。したがって、これは実際には[`Tangent`](@ref)です:

```jldoctest frule
julia> Δsincosx
Tangent{Tuple{Float64, Float64}}(0.6795498147167869, -0.7336293678134624)
```

オプションの[`RuleConfig`](@ref)オプションは、指定された機能をサポートするADシステムのためにのみfruleを指定することを可能にします。必要ない場合は省略でき、`frule`はフォールバックとしてヒットします。これはほとんどのルールに当てはまります。

参照: [`rrule`](@ref), [`@scalar_rule`](@ref), [`RuleConfig`](@ref)

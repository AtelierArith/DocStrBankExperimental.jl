```
rrule([::RuleConfig,] f, x...)
```

`x`をタプル`(x₁, x₂, ...)`として表現し、`f(x...)`の出力タプルを`Ω`とした場合、次のタプルを返します：

```julia
(Ω, (Ω̄₁, Ω̄₂, ...) -> (s̄elf, x̄₁, x̄₂, ...))
```

ここで、2番目の返り値は伝播ルールまたはプルバックです。これは、出力に対応するコタンジェント（`x̄₁, x̄₂, ...`）と、関数自体の内部値（クロージャ用の`s̄elf`）を受け取ります。

`rrule(f, xs...)`に一致するメソッドが定義されていない場合は、`nothing`を返します。

例：

単項入力、単項出力スカラー関数：

```jldoctest
julia> x = rand();

julia> sinx, sin_pullback = rrule(sin, x);

julia> sinx == sin(x)
true

julia> sin_pullback(1) == (NoTangent(), cos(x))
true
```

二項入力、単項出力スカラー関数：

```jldoctest
julia> x, y = rand(2);

julia> hypotxy, hypot_pullback = rrule(hypot, x, y);

julia> hypotxy == hypot(x, y)
true

julia> hypot_pullback(1) == (NoTangent(), (x / hypot(x, y)), (y / hypot(x, y)))
true
```

オプションの[`RuleConfig`](@ref)オプションは、指定された機能をサポートするADシステムのためにのみrrulesを指定することを可能にします。必要ない場合は省略でき、`rrule`はフォールバックとしてそれなしで呼び出されます。これはほとんどのルールに当てはまります。

関連情報：[`frule`](@ref)、[`@scalar_rule`](@ref)、[`RuleConfig`](@ref)

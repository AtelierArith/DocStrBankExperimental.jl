```
@non_differentiable(signature_expression)
```

メソッドが微分不可能であることを宣言するのを簡単にするためのヘルパーです。これは、すべての部分（関数 `s̄elf`-部分自体を含む）に対して [`NoTangent()`](@ref) を返す [`frule`](@ref) と [`rrule`](@ref) を定義するための短縮形です。

キーワード引数は含めるべきではありません。

```jldoctest
julia> @non_differentiable Base.:(==)(a, b)

julia> _, pullback = rrule(==, 2.0, 3.0);

julia> pullback(1.0)
(NoTangent(), NoTangent(), NoTangent())
```

シグネチャに型制約を置くことができます：

```jldoctest
julia> @non_differentiable Base.length(xs::Union{Number, Array})

julia> frule((ZeroTangent(), 1), length, [2.0, 3.0])
(2, NoTangent())
```

!!! 警告     このヘルパーマクロは、単純な一般的なケースのみをカバーしています。`where`-句はサポートしていません。これらについては、`rrule` と `frule` を直接宣言することができます。

```
Tensor{T<:Tuple}

Tensor{T}(xs...) where T
Tensor(xs...)
```

型 `Tensor` は純粋なテンソルを表します。

一般的なテンソルは純粋なテンソルの線形結合であり、`tensor` を使用して便利に作成できます。`LinearCombinations` は純粋なテンソルを基底要素として取ります。

`Tensor` は `Tuple` から、または個々のコンポーネントから作成できます。テンソルがタプルを唯一のコンポーネントとして持つ場合、2番目の形式は利用できません。

`Tensor` は [反復](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-iteration) および [インデックス付け](https://docs.julialang.org/en/v1/manual/interfaces/#Indexing) インターフェースを実装しています。これにより、例えばテンソルに対してスプラッティングが可能になり、`t::Tensor` の `i` 番目のコンポーネントには `t[i]` としてアクセスできます。

テンソルはネスト可能です。異なる括弧付けは異なるテンソルを生み出します。テンソルの再配置を容易にするために、`cat`、`flatten`、`swap`、および `regroup` の関数が提供されています。

`Tensor` の型パラメータは常に `Tuple` であることに注意してください。例えば、型 `T1` と `T2` の2つのコンポーネントを持つ `Tensor` の型は `Tensor{Tuple{T1,T2}}` であり、`Tensor{T1,T2}` ではありません。

他にも [`tensor`](@ref)、[`cat`](@ref)、[`flatten`](@ref)、[`regroup`](@ref)、[`swap`](@ref) を参照してください。

# 例

```jldoctest
julia> t = Tensor('x', 'y', "z")
'x'⊗'y'⊗"z"

julia> typeof(t)
Tensor{Tuple{Char, Char, String}}

julia> Tuple(t)
('x', 'y', "z")

julia> length(t), t[2], t[end]
(3, 'y', "z")

julia> a = Linear('x' => 1, 'y' => 2)
Linear{Char, Int64} with 2 terms:
'x'+2*'y'

julia> b = Linear(Tensor('x', 'z') => 1, Tensor('y', 'z') => 2)
Linear{Tensor{Tuple{Char, Char}}, Int64} with 2 terms:
2*'y'⊗'z'+'x'⊗'z'

julia> b == tensor(a, 'z')
true

julia> [uppercase(x) for x in t]
3-element Vector{Any}:
 'X': ASCII/Unicode U+0058 (category Lu: Letter, uppercase)
 'Y': ASCII/Unicode U+0059 (category Lu: Letter, uppercase)
 "Z"

julia> f((x1, xs...)::Tensor) = x1
f (generic function with 1 method)

julia> f(t)
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> t == Tensor(Tensor('x', 'y'), "z")
false

julia> a = tensor(); a[Tensor()]
1
```

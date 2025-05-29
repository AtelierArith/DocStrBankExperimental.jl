```
composeformulas(c::Connective, φs::NTuple{N,F})::F where {N,F<:Formula}
```

接続詞 `c` を介して同じ型の `N` 個の式を合成することによって、型 `F` の新しい式を返します。この関数は、式を柔軟に合成するために接続詞を使用することを可能にします（*実装* セクションを参照）。

# 例

```julia-repl
julia> f = parseformula("◊(p→q)");

julia> p = Atom("p");

julia> ∧(f, p)  # 式を合成する簡単な方法
SyntaxBranch: ◊(p → q) ∧ p

julia> f ∧ ¬p   # 中置記法を活用 ;) (see https://stackoverflow.com/a/60321302/5646732)
SyntaxBranch: ◊(p → q) ∧ ¬p

julia> ∧(f, p, ¬p) # ∧(f, ∧(p, ¬p)) のショートカット
SyntaxBranch: ◊(p → q) ∧ p ∧ ¬p
```

# 実装

`composeformulas` の上には、接続詞を使用して式や構文トークン（例：原子）を合成する柔軟な方法があります。これは以下のようなメソッドによって提供されます：

```
function (c::Connective)(φs::NTuple{N,Formula}) where {N}
    ...
end
```

これにより、`∧(f, ¬p)` のように式を合成することができ、新しく定義された `Formula` のサブタイプでこの合成にアクセスするためには、`composeformulas` の新しいメソッドを定義し、他の `Formula` からの昇格/降格も考慮する必要があります（[こちら](https://docs.julialang.org/en/v1/manual/conversion-and-promotion/)と[こちら](https://github.com/JuliaLang/julia/blob/master/base/promotion.jl)を参照）。

同様に、（おそらく新しく定義された）接続詞がその引数の数とは異なる数の構文トークン/式に適用されることを許可するために、新しく定義された接続詞 `c` に対して、上記の2つのメソッドに似た新しいメソッドを定義する必要があります。例えば、∧ と ∨ は二項であるため（すなわち、引数の数は2に等しい）、`∧(f, f2, f3, ...)` や `∨(f, f2, f3, ...)` のような合成は、SoleLogicsで定義された以下の2つのメソッドのおかげで可能です：

```
function ∧(
    c1::Formula,
    c2::Formula,
    c3::Formula,
    cs::Formula...
)
    return ∧(c1, ∧(c2, c3, cs...))
end
function ∨(
    c1::Formula,
    c2::Formula,
    c3::Formula,
    cs::Formula...
)
    return ∨(c1, ∨(c2, c3, cs...))
end
```

!!! 注     異なる型の `Formula` の合成を許可するために、昇格ルールを提供する必要があります。

[`Formula`](@ref) や [`Connective`](@ref) も参照してください。

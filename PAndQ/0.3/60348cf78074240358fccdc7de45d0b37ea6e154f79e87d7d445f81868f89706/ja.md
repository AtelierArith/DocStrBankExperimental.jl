```
tseytin(p)
```

与えられた命題に[Tseytin変換](https://en.wikipedia.org/wiki/Tseytin_transformation)を適用します。

命題を論理積標準形に変換するために[`normalize`](@ref)関数を使用すると、指数関数的に大きな命題が生成される可能性があり、十分に大きな命題に対しては扱いきれなくなることがあります。Tseytin変換は、論理積標準形であり、元の命題に対して[`is_equisatisfiable`](@ref)である線形に大きな命題を生成します。ただし、導入された変数が含まれており、元の命題の[`solutions`](@ref)のサブセットを生成します。

# 例

```jldoctest
julia> is_equisatisfiable(⊤, tseytin(⊤))
true

julia> @atomize is_equisatisfiable(p, tseytin(p))
true

julia> is_equisatisfiable(⊥, tseytin(⊥))
true
```

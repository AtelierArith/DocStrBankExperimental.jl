```julia
Compound(str::AbstractString) -> ChemEquations.Compound

```

`str`から化合物を構築します。

元素は大文字のUnicode文字で始まり、小文字のUnicode文字またはUnicode記号で終わります。

!!! info
    元素は、記号が最初の文字である場合、記号で始まることもできます（例: `"⬡H"`）。


解析は空白やアンダースコア（`_`）に対して無関心ですが、状態記号（`(s)`, `(l)`, `(g)`, `(aq)`）にも無関心です。特別な解析が実装されています：

  * 括弧（例: `"(CH3COO)2Mg"`)
  * `"*"`を含む化合物（例: `"CuSO4 * 5H2O"`)
  * 電子（`"e"`）

電荷は`"{±n}"`または`"{n±}"`の形式です。電子（`"e"`）については自動的に推測されます。

# 例

```jldoctest
julia> Compound("H2O(s)")
H2O

julia> Compound("H3O{+}")
H3O{+}

julia> Compound("(CH3COO)2Mg")
C4H6O4Mg

julia> Compound("CuSO4 * 5H2O")
CuSO9H10

julia> Compound("⬡Cl")
⬡Cl
```

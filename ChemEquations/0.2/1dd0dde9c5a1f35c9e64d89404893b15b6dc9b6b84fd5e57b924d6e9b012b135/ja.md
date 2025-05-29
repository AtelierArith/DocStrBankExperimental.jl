```julia
string(equation::ChemEquations.ChemEquation) -> String

```

化学方程式を表す文字列を作成します。

すべての化合物は[`Base.string(::Compound)`](@ref)を使用して表示され、元々与えられた順序で表示され、係数が1のものは表示されません。`'='`と`'+'`は区切りとして使用され、読みやすさのためにスペースが挿入されます。

# 例

```jldoctest
julia> string(ce"Cr2O7{2-} + H{+} + {-} = Cr{3+} + H2O")
"Cr2O7{-2} + H{+} + e = Cr{+3} + H2O"
```

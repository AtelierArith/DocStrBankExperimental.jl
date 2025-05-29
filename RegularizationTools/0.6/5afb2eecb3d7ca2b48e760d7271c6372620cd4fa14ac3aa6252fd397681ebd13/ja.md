```
to_general_form(Ψ::RegularizationProblem, b::AbstractVector, x̄::AbstractVector)
```

標準形で計算された解 $\bar {\rm x}$ を一般形 ${\rm x}$ に戻します（Hansen, 1998）。

$$
{\rm x}={\rm {\bf L^{+}_A}\bar{x} + x\_0}
$$

行列とベクトルは [RegularizationProblem](@ref) で定義されています。

使用例（通常の構文）

```julia
x = to_general_form(Ψ, b, x̄) 
```

使用例（遅延構文）

```julia
x = @>> x̄ to_general_form(Ψ, b) 
```

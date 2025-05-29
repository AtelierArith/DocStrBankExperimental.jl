```
状態
```

すべてのサンプリングされた状態の抽象スーパタイプ: `state <: State`。

# 例

## サンプリング可能なすべての状態を見つける

```julia-repl
julia> subtypes(State)

6-element Vector{Any}:
Bogoliubov
Coherent
Crescent
Fock
Squeezed
Thermal
```

## 特定の状態（真空）を作成してサンプリングする

```julia-repl
julia> s = Fock(0)
Fock(0)
julia> wigner(s,100)
┌ Warning: Fock state sampling for W is only valid for n ≫ 1.
```

ここでは、Fockサンプリングが小さな `n` に対しては明確に定義されていないため、警告が生成されます。

真空をサンプリングするより簡単な方法は 

```julia-repl
julia> s = Coherent(0) 
Coherent(0.0 + 0.0im)  # ComplexF64への型変換。

julia> wigner(s,100)
(ComplexF64[0.33820868828162637 + 0.4407579103538181im, 0.057183146091823775 - 0.2772571883006981im, ...
```

複素平面内のサンプリングされた点 `α,α⁺` の2つのベクトルを生成します。この場合、`α = conj(α⁺)` であり、倍増した位相空間で作業していないためです。

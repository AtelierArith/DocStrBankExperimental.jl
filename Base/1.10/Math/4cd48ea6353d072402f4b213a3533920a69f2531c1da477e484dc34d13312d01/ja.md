```
log(x)
```

`x`の自然対数を計算します。負の[`Real`](@ref)引数に対しては[`DomainError`](@ref)をスローします。複素数の負の引数を使用して複素数の結果を得てください。

関連情報としては[`ℯ`](@ref)、[`log1p`](@ref)、[`log2`](@ref)、[`log10`](@ref)があります。

# 例

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log(2)
0.6931471805599453

julia> log(-3)
ERROR: DomainError with -3.0:
logは負の実引数で呼び出されましたが、複素数引数で呼び出された場合にのみ複素数の結果を返します。log(Complex(x))を試してください。
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]

julia> log.(exp.(-1:1))
3-element Vector{Float64}:
 -1.0
  0.0
  1.0
```

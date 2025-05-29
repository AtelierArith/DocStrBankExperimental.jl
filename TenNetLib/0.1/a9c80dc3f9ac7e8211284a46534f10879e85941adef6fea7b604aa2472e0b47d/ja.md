```
function measure(::Type{ElT} = ComplexF64, psi::MPS, opstr::String; kwargs...)
```

与えられた MPS `psi::MPS` に対する指定された演算子名 (`opstr::String`) の (複素数 / 実数) の局所期待値 (`::Vector{ComplexF64}` / `::Vector{Float64}`) をすべてのサイトで返します。

オプションとして、特定のサイトについては、キーワード引数 `sites` を指定できます。例えば、`sites = [1, 2, 3]` のように。

`ElT = Float64` の場合、期待値が複素数であると警告が発生します！

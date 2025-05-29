```
function measure(::Type{ElT} = ComplexF64, psi::TTN, oppairs::Vector{Pair{String, Int}};
                 isfermions::Bool = true)
```

与えられたTTN `psi::TTN`の（複素数/実数）マルチサイト期待値（`::ComplexF64` / `::Float64`）を返します。`oppairs::Vector{Pair{String, Int}}`は演算子名（`String`）とサイト位置（`Int`）のペアを含みます。例えば、<ψ|OᵢOⱼOₖ... |ψ>の場合、`oppairs = ["O" => i, "O" => j, "O" => k,...]`となります。

フェルミオン演算子の場合、`isfermions::Bool = true`（デフォルト）であれば、フェルミオンJW文字列が自動的に追加されます。

`ElT = Float64`の場合、期待値が複素数であると警告が発生します！

#### 例:

```
valueC = measure(psi, ["Cdag" => 2, "C" => 6, "Cdag" => 9, "C" => 12])
valueR = measure(Float64, psi, ["Cdag" => 2, "C" => 6, "Cdag" => 9, "C" => 12])
```

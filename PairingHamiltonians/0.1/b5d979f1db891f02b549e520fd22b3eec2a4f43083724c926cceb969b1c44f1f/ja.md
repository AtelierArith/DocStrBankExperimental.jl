```
eval_Hamil(method::String, basis::Vector{Int}, eps::Vector{Float64}, g::Float64, Nq::Int, degenerate::Bool; debug_mode::Int=0, sparce_rep::Bool=false)::Tuple{Matrix{Float64}, Matrix{Float64}, Union{Matrix{Float64}, Dict{UInt64, Float64}}}
```

ハミルトニアン行列要素を評価する関数。軌道の数と占有状態の数が与えられると、フル行列表現またはスパース表現でハミルトニアン行列要素を準備できます。より大きなシステムでは、フル行列を保存する代わりに `Dict{UInt64, Float64}` を使用したスパース表現が使用されます。辞書のキーは、多体構成の整数表現に対応しています。

注意してください、`"1"` と `'1'` はJuliaでは異なります。前者は文字列であり、後者は文字です。

```
JuMP.lp_sensitivity_report(model::InfiniteModel; 
                           [atol::Float64 = 1e-8])::InfOptSensitivityReport
```

`JuMP.lp_sensitivity_report`を拡張して、最適化モデルに従ったLP感度レポートを生成し、返します。構文の詳細については、[`InfOptSensitivityReport`](@ref)を参照してください。`atol`は最適性許容誤差を示し、基準を計算するためにソルバーが使用するものと一致する必要があります。レポートの出力を解釈するためのより技術的な情報については、`JuMP`のドキュメントを参照してください。

**例**

```julia-repl
julia> report = lp_sensitivity_report(model);

julia> report[x]
(0.0, 0.5)
```

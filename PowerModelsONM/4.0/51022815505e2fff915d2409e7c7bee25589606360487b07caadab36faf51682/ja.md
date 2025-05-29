```
optimize_switches(
    network::Dict{String,<:Any},
    solver;
    formulation::Type=PMD.LPUBFDiagPowerModel,
    algorithm::String="full-lookahead"
)::Dict{String,Any}
```

  * `algorithm::String`が`"rolling-horizon"`の場合、マルチネットワークデータ構造`network`内のすべてのサブネットワークを順番に反復し、最適なスイッチング/MLD問題を逐次的に解決し、解決されたタイムステップから新しいスイッチ構成とストレージエネルギーで次のタイムステップを更新します。それ以外の場合、`"full-lookahead"`であれば、すべてのタイムステップを単一の最適化問題で解決します（デフォルト: `"full-lookahead"`）

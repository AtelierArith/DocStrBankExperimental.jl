```
get_timestep_fault_currents(
    fault_studies_results::Dict{String,<:Any},
    faults::Dict{String,<:Any},
    network::Dict{String,<:Any};
    ret_protection_only::Bool=false
)::Vector{Dict{String,Any}}
```

各タイムステップにおける故障研究の結果に関する情報を取得します。これには以下が含まれます：

  * 故障に関する情報、例えば

      * アドミタンス（`"conductance (S)"`および`"susceptance (S)"`）
      * 故障が適用されるバス
      * 故障の種類（3p、3pg、llg、ll、lg）
      * 故障が適用される接続
  * ネットワークの保護状態に関する情報、例えば

      * 故障電流 `|I| (A)`
      * ゼロシーケンス故障電流 `|I0| (A)`
      * 正のシーケンス故障電流 `|I1| (A)`
      * 負のシーケンス故障電流 `|I2| (A)`
      * スイッチの送信側からのバス電圧 `|V| (V)`
      * スイッチの送信側からのバス電圧角度 `phi (deg)`

`ret_protection_only==false` は、スイッチ=yのすべてのラインに対して電流と電圧を返すべきことを示し、`true` の場合は保護装置が定義されているスイッチ（リクローザー、リレー、ヒューズ）のみを返すべきことを示します。

```
patient_data()
```

Laleh et al. [(2022)](https://doi.org/10.1371/journal.pcbi.1009822) "Classical mathematical models for prediction of response to chemotherapy and immunotherapy", *PLOS Computational Biology* で収集された病変測定データを行テーブル形式で返します。

各行は、ユニークな患者の単一病変に対するすべての測定を表します。

```julia
record = first(patient_data())

julia> record.Pt_hashID # 患者識別子
"0218075314855e6ceacca856fcd4c737-S1"

julia> record.T_weeks # 測定時期（週単位）
7-element Vector{Float64}:
  0.1
  6.0
 12.0
 17.0
 23.0
 29.0
 35.0

julia> record.Lesion_normvol # データセットの最大値で正規化されたすべての体積
7-element Vector{Float64}:
 0.000185364052636979
 0.00011229838600811
 8.4371439525252e-5
 8.4371439525252e-5
 1.05464299406565e-5
 2.89394037571615e-5
 8.4371439525252e-5
```

[`flat_patient_data`](@ref) も参照してください。

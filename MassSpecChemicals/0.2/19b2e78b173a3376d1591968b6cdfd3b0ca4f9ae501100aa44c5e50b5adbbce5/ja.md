```
isobars_rt(ion::AbstractChemical, lib::AbstractVector{T}; rt_tol = 0.3, mz_tol = crit(0.01, 20e-6))
isobars_rt(ion::AbstractChemical, lib::Table; libchemical = :AdductIon, libmz = :MZ, librt = :RT, rt_tol = 0.3, mz_tol = crit(0.01, 20e-6))
```

`lib`のサブベクターを返し、すべての要素が特定のrtおよびmzの許容範囲内で`ion`と同じ質量を持つ。 

キーワード引数`libchemical`、`libmz`、および`librt`は、`AdductIon`オブジェクトの列、m/z値、およびrt値を指定します。 

許容範囲は数値または基準であり、最大許容差を表します。複数の許容範囲を持つ基準の場合、それらのいずれかに含まれることは基準を満たすと見なされます。

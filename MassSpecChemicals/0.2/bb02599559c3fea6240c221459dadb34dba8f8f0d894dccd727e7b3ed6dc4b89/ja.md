```
isobars_rt_table(ion::AbstractChemical, lib::AbstractVector{T}; rt_tol = 0.3, mz_tol = crit(0.01, 20e-6))
isobars_rt_table(exp::Vector, lib::AbstractVector{T}; kwargs...)
isobars_rt_table(exp::Table, lib::AbstractVector{T}; expid = true, expchemical = :AdductIon, expmz = :MZ, exprt = :RT, rt_tol = 0.3, mz_tol = crit(0.01, 20e-6))
isobars_rt_table(ion::AbstractChemical, lib::Table; libid = true, libchemical = :AdductIon, libmz = :MZ, librt = :RT, rt_tol = 0.3, mz_tol = crit(0.01, 20e-6))
isobars_rt_table(exp::Vector, lib::Table; libid = true, libchemical = :AdductIon, libmz = :MZ, librt = :RT, rt_tol = 0.3, mz_tol = crit(0.01, 20e-6))
isobars_rt_table(exp::Table, lib::Table; expid = true, expchemical = :AdductIon, expmz = :MZ, exprt = :RT, libid = true, libchemical = :AdductIon, libmz = :MZ, librt = :RT, rt_tol = 0.3, mz_tol = crit(0.01, 20e-6))
```

`lib`からのイオンを表すすべての行を返す`Table`を返します。これらのイオンは`ion`と同じアイソバリックであるか、特定のrtおよびmzの許容範囲内にある`exp`からのイオンです。

許容範囲は数値または基準であり、最大許容差を表します。複数の許容範囲を持つ基準の場合、それらのいずれかに含まれていることが基準を満たすと見なされます。

キーワード引数`libchemical`、`libmz`、および`librt`は、`lib`からのAdductIonオブジェクト、m/z値、およびrt値の列を指定します。

キーワード引数`expchemical`、`expmz`、および`exprt`は、`exp`からのAdductIonオブジェクト、m/z値、およびrt値の列を指定します。

キーワード引数`libid`と`expid`は、`lib`または`exp`の行IDを格納する列を作成するかどうかを決定します。

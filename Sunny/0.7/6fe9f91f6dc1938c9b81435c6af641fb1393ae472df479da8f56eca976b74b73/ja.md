```
SampledCorrelationsStatic(sys::System; measure)
```

静的ペア相関のサンプルを蓄積するためのオブジェクトです。これは[`SampledCorrelations`](@ref)に似ていますが、[`add_sample!`](@ref)の呼び出し時に時間積分は行われません。結果として得られるオブジェクトは、古典的ボルツマン分布から統計を計算するために[`intensities_static`](@ref)と共に使用できます。ただし、動的[`intensities`](@ref)データは利用できません。同様に、励起スペクトルに依存する古典から量子への補正も行うことはできません。

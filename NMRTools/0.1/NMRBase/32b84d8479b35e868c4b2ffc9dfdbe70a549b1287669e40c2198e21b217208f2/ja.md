```
TimeDimension <: NonFrequencyDimension <: NMRDimension
```

NMRDataオブジェクトで使用される時間次元の抽象スーパタイプ。周波数の進化を表す時間領域のために、具体的なタイプ`T1Dim`、`T2Dim`、`T3Dim`、および`T4Dim`が生成され、緩和および実時間の動力学を表すために`TrelaxDim`と`TkinDim`が生成されます。

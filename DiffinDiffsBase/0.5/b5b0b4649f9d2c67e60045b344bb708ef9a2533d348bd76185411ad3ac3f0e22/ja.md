```
DynamicTreatment{S<:TreatmentSharpness} <: AbstractTreatment
```

時間の経過に伴って効果が進化することが許可された吸収バイナリ治療を指定します。詳細は[`dynamic`](@ref)を参照してください。

# フィールド

  * `time::Symbol`: カレンダー時間を表すデータの列名。
  * `exc::Tuple{Vararg{Int}}`: 除外された相対時間。
  * `s::S`: [`TreatmentSharpness`](@ref)のインスタンス。

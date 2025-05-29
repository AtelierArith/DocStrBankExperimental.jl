```
mutable struct BranchImpedanceChange <: Perturbation
    time::Float64
    branch_type::Type{<:PSY.ACBranch}
    branch_name::String
    multiplier::Float64
end
```

BranchImpedanceChangeは、ユーザー定義の乗数によってブランチのインピーダンスを変更します。現在、静的ブランチの切断、`PowerSystems.Line`および`PowerSystems.Transformer2W`のみがサポートされています。将来のリリースでは、動的ラインの切断のサポートが提供される予定です。

# 引数:

  * `time::Float64` : ブランチインピーダンス変更が発生する時点を定義します。この時間はシミュレーションで考慮される時間範囲内である必要があります。
  * `branch_tipe::Type{<:PowerSystems.ACBranch}` : 修正されるブランチのタイプ
  * `branch_name::String` : ブランチを識別するためのユーザー定義名
  * `multiplier::Float64` : インピーダンス乗数のためのユーザー定義値。

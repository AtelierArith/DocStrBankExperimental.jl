```
mutable struct BranchTrip <: Perturbation
    time::Float64
    branch_type::Type{<:PowerSystems.ACBranch}
    branch_name::String
end
```

`BranchTrip`はブランチをシステムから完全に切り離します。現在、静的ブランチの切断、`PowerSystems.Line`および`PowerSystems.Transformer2W`のみがサポートされています。将来のリリースでは、動的ラインの切断のサポートが提供される予定です。**注意:** `PowerSimulationsDynamics.jl`ではアイランド化は現在サポートされていません。`BranchTrip`が発電ユニットを孤立させると、孤立した発電機のためにシステムが発散する可能性があります。

# 引数:

  * `time::Float64` : ブランチトリップが発生する時刻を定義します。この時刻はシミュレーションで考慮される時間範囲内である必要があります。
  * `branch_tipe::Type{<:PowerSystems.ACBranch}` : 切断されたブランチのタイプ
  * `branch_name::String` : ブランチを識別するためのユーザー定義名

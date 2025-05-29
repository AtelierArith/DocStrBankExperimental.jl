```julia
struct ProposalTune{F<:Real, U<:BaytesCore.UpdateBool, T<:BaytesCore.DataTune}
```

提案関数調整構造体。

アルゴリズムの提案ステップに関する情報を含み、異なるサンプラー間で共有される高レベルのものであり、アルゴリズム構造体には保存されません。

# フィールド

  * `temperature::Real`: 対数目的温度の調整用の温度。
  * `update::BaytesCore.UpdateBool`: 提案ステップの前に新しいパラメータでアルゴリズムを更新する必要があるかどうかの準Boolean。
  * `datatune::BaytesCore.DataTune`: 現在データインデックスがどのイテレーションにあるかの情報。

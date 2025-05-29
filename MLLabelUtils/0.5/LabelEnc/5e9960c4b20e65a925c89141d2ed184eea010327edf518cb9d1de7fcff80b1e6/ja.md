サブモジュール `MLLabelUtils.LabelEnc` には、人気のあるラベルエンコーディングの選択肢が含まれています：

厳密なバイナリラベルエンコーディング：

  * [`LabelEnc.FuzzyBinary`](@ref)
  * [`LabelEnc.TrueFalse`](@ref)
  * [`LabelEnc.ZeroOne`](@ref)
  * [`LabelEnc.MarginBased`](@ref)

マルチクラスラベルエンコーディング：

  * [`LabelEnc.Indices`](@ref)
  * [`LabelEnc.NativeLabels`](@ref)
  * [`LabelEnc.OneOfK`](@ref)

マルチクラスからバイナリへ：

  * [`LabelEnc.OneVsRest`](@ref)

```julia
struct CommonConvWrapper{T<:DistributedFactorGraphs.AbstractFactor, VT<:Tuple, TP<:(Base.RefValue{<:Tuple}), CT, AM<:ManifoldsBase.AbstractManifold, HR<:IncrementalInference.HypoRecipeCompute, MT, G} <: DistributedFactorGraphs.FactorOperationalMemory
```

推論操作中に使用される主要な因子メモリコンテナ – すなわち、1つの完全な畳み込み操作に特有の値

注意事項

  * CCWはシリアル化されず、永続化されません
  * 執筆時点では、因子ごとに1つのCCWがあるという前提です
  * マルチスレッド設計は、CCW内のサブコンテナとして、またはそれ以外の方法で、別々のメモリを保持する必要があります。
  * #467以降、`CalcFactor`は`getSample`または関数残差計算中に「ユーザーが見る」唯一のタイプです `(cf::CalcFactor{<:MyFactor})`、すなわち`MyFactor <: AbstractRelative___`
  * 可能な限り同じメカニズムを使用してパラメトリック計算のための`CalcFactorMahalanobis`も存在します。
  * CCWは、他の以前のタイプ、FMD CPT CF CFMの統合オブジェクトです。

関連 

[`CalcFactor`](@ref), [`CalcFactorMahalanobis`](@ref)

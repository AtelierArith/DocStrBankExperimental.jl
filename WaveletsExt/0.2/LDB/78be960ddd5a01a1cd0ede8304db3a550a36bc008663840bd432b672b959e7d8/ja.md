```
LocalDiscriminantBasis
```

ローカル判別基底 (LDB) のクラスタイプで、N. Saito と R. Coifman によって「Local Discriminant Bases and Their Applications」で開発された特徴選択アルゴリズムです。これは、Journal of Mathematical Imaging and Vision, Vol 5, 337-358 (1995) に掲載されています。この構造体には以下のフィールド値が含まれています：

# パラメータと属性：

  * `wt::DiscreteWavelet`: (デフォルト: `wavelet(WT.haar)`) 変換目的のための離散ウェーブレット。
  * `max_dec_level::Union{Integer, Nothing}`: (デフォルト: `nothing`) 計算されるウェーブレットパケット分解の最大レベル。
  * `dm::DiscriminantMeasure`: (デフォルト: `AsymmetricRelativeEntropy()`) LDBアルゴリズムのための判別測度。サポートされている測度は `AsymmetricRelativeEntropy()`, `LpDistance()`, `SymmetricRelativeEntropy()`, および `HellingerDistance()` です。
  * `en::EnergyMap`: (デフォルト: `TimeFrequency()`) 使用されるエネルギーマップのタイプ。サポートされているマップは `TimeFrequency()`, `ProbabilityDensity()`, および `Signatures()` です。
  * `dp::DiscriminantPower()`: (デフォルト: `BasisDiscriminantMeasure()`) 拡張係数間の判別力の測度。サポートされている測度は `BasisDiscriminantMeasure()`, `FishersClassSeparability()`, および `RobustFishersClassSeparability()` です。
  * `top_k::Union{Integer, Nothing}`: (デフォルト: `nothing`) 各ノードで判別測度を決定するために使用されるトップk係数。
  * `n_features::Union{Integer, Nothing}`: (デフォルト: `nothing`) 特徴選択と変換を経た後の出力の次元。
  * `sz::Union{Vector{T} where T<:Integer, Nothing}`: (デフォルト: `nothing`) 信号のサイズ
  * `Γ::Union{AbstractArray{T} where T<:AbstractFloat, AbstractArray{NamedTuple{(:coef, :weight), Tuple{S₁, S₂}}} where {S₁<:Array{T} where T<:AbstractFloat, S2<:Union{T, Array{T}} where T<:AbstractFloat}, Nothing}`: (デフォルト: `nothing`) 計算されたエネルギーマップ
  * `DM::Union{AbstractArray{<:AbstractFloat}, Nothing}`: (デフォルト: `nothing`) 計算された判別測度
  * `cost::Union{AbstractVector{<:AbstractFloat}, Nothing}`: (デフォルト: `nothing`) 判別測度 `DM` に基づく計算されたウェーブレットパケット分解 (WPD) ツリーコスト。
  * `tree::Union{BitVector, Nothing}`: (デフォルト: `nothing`) 判別測度 `DM` に基づく計算された最良の WPD ツリー。
  * `DP::Union{AbstractVector{<:AbstractFloat}, Nothing}`: (デフォルト: `nothing`) 計算された判別力
  * `order::Union{AbstractVector{Integer}, Nothing}`: (デフォルト: `nothing`) 降順での `DP` の順序。

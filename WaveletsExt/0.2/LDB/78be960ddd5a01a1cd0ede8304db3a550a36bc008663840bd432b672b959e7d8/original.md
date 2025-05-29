```
LocalDiscriminantBasis
```

Class type for the Local Discriminant Basis (LDB), a feature selection algorithm developed by N. Saito and R. Coifman in "Local Discriminant Bases and Their Applications" in the Journal of Mathematical Imaging and Vision, Vol 5, 337-358 (1995). This struct contains the following field values: 

# Parameters and Attributes:

  * `wt::DiscreteWavelet`: (Default: `wavelet(WT.haar)`) A discrete wavelet for transform purposes.
  * `max_dec_level::Union{Integer, Nothing}`: (Default: `nothing`) Max level of wavelet packet decomposition to be computed.
  * `dm::DiscriminantMeasure`: (Default: `AsymmetricRelativeEntropy()`) the discriminant   measure for the LDB algorithm. Supported measures are the `AsymmetricRelativeEntropy()`,   `LpDistance()`, `SymmetricRelativeEntropy()`, and `HellingerDistance()`.
  * `en::EnergyMap`: (Default: `TimeFrequency()`) the type of energy map used. Supported maps   are `TimeFrequency()`, `ProbabilityDensity()`, and `Signatures()`.
  * `dp::DiscriminantPower()`: (Default: `BasisDiscriminantMeasure()`) the measure of   discriminant power among expansion coefficients. Supported measures are   `BasisDiscriminantMeasure()`, `FishersClassSeparability()`, and   `RobustFishersClassSeparability()`.
  * `top_k::Union{Integer, Nothing}`: (Default: `nothing`) the top-k coefficients used in each   node to determine the discriminant measure.
  * `n_features::Union{Integer, Nothing}`: (Default: `nothing`) the dimension of output after   undergoing feature selection and transformation.
  * `sz::Union{Vector{T} where T<:Integer, Nothing}`: (Default: `nothing`) Size of signal
  * `Γ::Union{AbstractArray{T} where T<:AbstractFloat, AbstractArray{NamedTuple{(:coef, :weight), Tuple{S₁, S₂}}} where {S₁<:Array{T} where T<:AbstractFloat, S2<:Union{T, Array{T}} where T<:AbstractFloat}, Nothing}`: (Default: `nothing`) computed energy map
  * `DM::Union{AbstractArray{<:AbstractFloat}, Nothing}`: (Default: `nothing`) computed discriminant measure
  * `cost::Union{AbstractVector{<:AbstractFloat}, Nothing}`: (Default: `nothing`) computed   wavelet packet decomposition (WPD) tree cost based on the discriminant measure `DM`.
  * `tree::Union{BitVector, Nothing}`: (Default: `nothing`) computed best WPD tree based on   the discriminant measure `DM`.
  * `DP::Union{AbstractVector{<:AbstractFloat}, Nothing}`: (Default: `nothing`) computed discriminant power
  * `order::Union{AbstractVector{Integer}, Nothing}`: (Default: `nothing`) ordering of `DP` by descending order.

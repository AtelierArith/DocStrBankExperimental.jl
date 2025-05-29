```
OrdinalPatterns <: OutcomeSpace
OrdinalPatterns{m}(τ = 1, lt::Function = ComplexityMeasures.isless_rand)
```

長さ`m`の順序置換パターンに基づく[`OutcomeSpace`](@ref)で、元々は[BandtPompe2002](@citet)の置換エントロピーに関する論文で紹介されました。`m`は型パラメータとして与えられるため、リテラル整数である場合にはパフォーマンスの向上が図られます。

[`probabilities`](@ref)に渡されると、出力は入力データ型に依存します：

  * **単変量データ**。単変量時系列（`AbstractVector`）に適用される場合、時系列はまず埋め込み遅延`τ`と次元`m`を使用して埋め込まれ、埋め込みベクトル$\{ \bf{x}_i \}_{i=1}^{N-(m-1)\tau}$が生成されます。次に、各$\bf{x}_i$について、その置換パターン$\pi_{i}$を見つけます。確率は、[`UniqueElements`](@ref)を使用してエンコードされた置換シンボルの頻度として推定されます。得られた確率を[`information`](@ref)に渡すと、元の置換エントロピーが計算されます[BandtPompe2002](@cite)。
  * **多変量データ**。`D`次元の`StateSpaceSet`に適用される場合、埋め込みは構築されず、`m`は`D`と等しく、`τ`は無視されます。データセットの各ベクトル$\bf{x}_i$は、$\bf{x}_i$の要素の相対的な大きさを比較することによって、その置換パターン$\pi_{i}$に直接マッピングされます。上記と同様に、確率は置換シンボルの頻度として推定されます。得られた確率は多変量置換エントロピーを計算するために使用できます[He2016](@cite)、ただしここでは置換パターンのさらなる細分化は行いません（[He2016](@citet)の図3のように）。

内部的に、[`OrdinalPatterns`](@ref)は[`OrdinalPatternEncoding`](@ref)を使用して、効率的な計算のために順序パターンを整数として表現します。

順序（ソート）パターンだけでなく、状態ベクトルの振幅に関する情報も組み込む推定器については、[`WeightedOrdinalPatterns`](@ref)および[`AmplitudeAwareOrdinalPatterns`](@ref)を参照してください。空間データで使用できるこの推定器のバージョンについては、[`SpatialOrdinalPatterns`](@ref)を参照してください。

!!! note "順序パターンにおける等しい値の取り扱い"
    [BandtPompe2002](@citet)では、等しい値は出現順に従って順序付けられますが、これは特に振幅解像度が低いデータに対して誤った時間的相関を引き起こす可能性があります[Zunino2017](@cite)。ここでは、デフォルトで、2つの値が等しい場合、1つがランダムに「最大」として割り当てられます。`lt = ComplexityMeasures.isless_rand`を使用します。[BandtPompe2002](@citet)からの動作を得るには、`lt = Base.isless`を使用してください。


## 結果空間

`OrdinalPatterns`の結果空間`Ω`は、整数`1, 2, …, m`によって形成される長さ`m`の順序パターン（すなわち置換）の集合です。そのようなパターンは`factorial(m)`個存在します。

例えば、結果`[2, 3, 1]`は、2番目の位置に最小値、3番目の位置に次に小さい値、1番目の位置に次に小さい、すなわち最大値を持つ順序パターンに対応します。[`OrdinalPatternEncoding`](@ref)も参照してください。

## インプレースシンボリゼーション

`OrdinalPatterns`は、ループシナリオでのアロケーションを削減するために、`StateSpaceSet`入力（または埋め込まれたベクトル入力）用のインプレース[`probabilities!`](@ref)も実装しています。事前に割り当てられたシンボルベクトルの長さはデータセットの長さと一致する必要があります。例えば

```julia
using ComplexityMeasures
m, N = 2, 100
est = OrdinalPatterns{m}(τ)
x = StateSpaceSet(rand(N, m)) # 一部の入力データセット
πs_ts = zeros(Int, N) # 長さは`x`の長さと一致する必要があります
p = probabilities!(πs_ts, est, x)
```

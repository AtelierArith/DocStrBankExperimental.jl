`AdaptiveResonance.jl`のメインモジュールは、適応共鳴理論アルゴリズムのJuliaパッケージです。

このモジュールは、`AdaptiveResonance.jl`パッケージで使用されるすべてのARTモジュール、オプション、およびユーティリティをエクスポートします。完全な使用法については、公式ガイドを参照してください https://ap6yc.github.io/AdaptiveResonance.jl/dev/man/guide/。

# 基本的な使い方

スクリプトでパッケージをインストールしてインポートするには、次のようにします。

```julia
using Pkg
Pkg.add("AdaptiveResonance")
using AdaptiveResonance
```

次に、デフォルトオプションでARTモジュールを作成します。

```julia
my_art = DDVFA()
```

または、キーワード引数を介してカスタムオプションを指定します。

```julia
my_art = DDVFA(rho_ub=0.45, rho_ub=0.7)
```

すべてのモデルを`train!`でトレーニングし、`classify`で推論を行います。バッチでは、サンプルはJuliaの列優先方式で解釈され、次元は`(n_dim, n_samples)`（すなわち、列がサンプル）です。

オプションのラベルをキーワード引数`y`として使用して、教師なしARTモジュールをインクリメンタルまたはバッチでトレーニングします。

```julia
# データを何らかの方法でロード
samples, labels = load_some_data()

# 教師なしバッチ
train!(my_art, samples)

# 教師ありバッチ
train!(my_art, samples, y=labels)

# 教師なしインクリメンタル
for ix in eachindex(labels)
    train!(my_art, samples[:, ix])
end

# 教師ありインクリメンタル
for ix in eachindex(labels)
    train!(my_art, samples[:, ix], y=labels[ix])
end
```

位置引数を使用して、教師ありARTMAPをトレーニングします。

```julia
my_artmap = SFAM()
train!(my_artmap, samples, labels)
```

どちらのモジュールでも、`classify(art, samples)`で推論を行います。

```julia
# バッチ推論
y_hat = classify(my_art, test_samples)

# インクリメンタル推論
for ix in eachindex(test_labels)
    y_hat[ix] = classify(my_artmap, test_samples[:, ix])
end
```

# インポート

次の名前は、パッケージによって依存関係としてインポートされます。

  * `Base`
  * `Core`
  * `Distributed`
  * `DocStringExtensions`
  * `ElasticArrays`
  * `Logging`
  * `NumericalTypeAliases`
  * `Parameters`
  * `Pkg`
  * `ProgressBars`
  * `SharedArrays`

# エクスポート

次の名前はエクスポートされ、パッケージを`using`したときに利用可能です。

  * [`ACTIVATION_FUNCTIONS`](@ref)
  * [`ADAPTIVERESONANCE_MODULES`](@ref)
  * [`ADAPTIVERESONANCE_VERSION`](@ref)
  * [`ART`](@ref)
  * [`ARTMAP`](@ref)
  * [`ARTMAP_MODULES`](@ref)
  * [`ARTModule`](@ref)
  * [`ARTOpts`](@ref)
  * [`ART_MODULES`](@ref)
  * [`DAM`](@ref)
  * [`DDVFA`](@ref)
  * [`DDVFA_METHODS`](@ref)
  * [`DVFA`](@ref)
  * [`DataConfig`](@ref)
  * [`FAM`](@ref)
  * [`FuzzyART`](@ref)
  * [`GammaNormalizedFuzzyART`](@ref)
  * [`MATCH_FUNCTIONS`](@ref)
  * [`SFAM`](@ref)
  * [`UPDATE_FUNCTIONS`](@ref)
  * [`artscene_filter`](@ref)
  * [`classify`](@ref)
  * [`complement_code`](@ref)
  * [`data_setup!`](@ref)
  * [`get_W`](@ref)
  * [`get_data_characteristics`](@ref)
  * [`linear_normalization`](@ref)
  * [`opts_DAM`](@ref)
  * [`opts_DDVFA`](@ref)
  * [`opts_DVFA`](@ref)
  * [`opts_FAM`](@ref)
  * [`opts_FuzzyART`](@ref)
  * [`opts_GammaNormalizedFuzzyART`](@ref)
  * [`opts_SFAM`](@ref)
  * [`performance`](@ref)
  * [`train!`](@ref)

```
fit_sfh(MH_model0::AbstractMetallicityModel,
        disp_model0::AbstractDispersionModel,
        models::AbstractMatrix{<:Number},
        data::AbstractVector{<:Number},
        logAge::AbstractVector{<:Number},
        metallicities::AbstractVector{<:Number};
        x0::AbstractVector{<:Number} = <...>
        kws...)
fit_sfh(MH_model0::AbstractMetallicityModel,
        disp_model0::AbstractDispersionModel,
        models::AbstractVector{<:AbstractMatrix{<:Number}},
        data::AbstractMatrix{<:Number},
        logAge::AbstractVector{<:Number},
        metallicities::AbstractVector{<:Number};
        x0::AbstractVector{<:Number} = <...>
        kws...)
```

[`CompositeBFGSResult`](@ref StarFormationHistories.CompositeBFGSResult) インスタンスを返し、提供された単純星団 (SSP) テンプレート `models`（対数年齢 `logAge = log10(age [yr])` と金属量 `metallicities` を持つ）を提供された `data` にフィッティングすることで得られた最大事後確率 (MAP) と最大尤度推定 (MLE) を含みます。金属量の進化は、提供された `MH_model0` を使用してモデル化され、そのパラメータは自由または固定可能であり、固定時間における金属量の分散は `disp_model0` によってモデル化され、そのパラメータも自由または固定可能です。

このメソッドは、`logAge` の `N` 個のユニークなエントリと `metallicities` の `M` 個のユニークなエントリの外積によって定義される星モデルのグリッドで最も効果的に機能するように設計されています。使用法の詳細については、例を参照してください。

私たちは、`MH_model0` に使用できる年齢-金属量関係および質量-金属量関係のいくつかのオプションを提供し、ユーザーがこの関数と統合できる新しいモデルを作成するためのAPIを定義します。金属量分散モデル `disp_model0` に対しても同様の柔軟性が許可されています。

主要なメソッドシグネチャは、`models` と `data` のフラットな形式を使用します。詳細については、[`StarFormationHistories.composite!`](@ref) のフラットな呼び出しシグネチャに関するノートや、`models` をこのフラットな形式に再配置するのを容易にする [`stack_models`](@ref StarFormationHistories.stack_models) を参照してください。

# 引数

  * `MH_model0` は、形成される星の平均金属量が時間とともにどのように変化するかを定義する [`AbstractMetallicityModel`](@ref StarFormationHistories.AbstractMetallicityModel) のインスタンスです。このインスタンスに含まれるフィッティング可能なパラメータは、最適化を開始するための初期値として使用されます。
  * `disp_model0` は、固定時間ビンで形成される星の金属量の分布を定義する [`AbstractDispersionModel`](@ref StarFormationHistories.AbstractDispersionModel) のインスタンスです。このインスタンスに含まれるフィッティング可能なパラメータは、最適化を開始するための初期値として使用されます。
  * `models` は、観測されたヘス図を構成する SSP のテンプレートヘス図です。
  * `data` は、観測データのヘス図です。
  * `logAge::AbstractVector{<:Number}` は、`models` のテンプレートを作成するために使用される星団の有効年齢を含むベクトルで、単位は `log10(age [yr])` です。たとえば、ある星団の年齢が 1 Myr の場合、その `logAge` のエントリは `log10(10^6) = 6.0` であるべきです。
  * `metallicities::AbstractVector{<:Number}` は、`models` のテンプレートを作成するために使用される星団の有効金属量を含むベクトルです。これらは [M/H] または [Fe/H] のような対数的な豊富さであるべきです。役立つかもしれない [Wikipedia](https://en.wikipedia.org/wiki/Metallicity) にいくつかのノートがあります。

# キーワード引数

  * `x0` は、`logAge` の *ユニーク* エントリごとの星の質量係数の初期推定値のベクトルです。合理的なデフォルトを設定しようとしますが、ほとんどの場合、ユーザーはこのキーワード引数を計算して渡すべきです。定常星形成率と総星質量を仮定して `x0` を準備するために [`StarFormationHistories.construct_x0_mdf`](@ref) を提供します。これは通常、良い初期推定です。
  * `kws...` は `Optim.Options` に渡され、収束のための許容誤差を制御するために使用できます。

# 戻り値

  * この関数は、MLE と MAP の最適化の両方からの出力を含む [`CompositeBFGSResult`](@ref StarFormationHistories.CompositeBFGSResult) を返し、`result.mle` および `result.map` を介してアクセス可能です。これらはそれぞれ [`BFGSResult`](@ref StarFormationHistories.BFGSResult) のインスタンスです。これらの構造体に関する詳細は、ドキュメントを参照してください。

```

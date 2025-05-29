```
generate_stars_mass(mini_vec::AbstractVector{<:Number},
                    mags, mag_names::AbstractVector{String},
                    limit::Number,
                    imf::Distributions.Sampleable{Distributions.Univariate, Distributions.Continuous};
                    dist_mod::Number=0,
                    rng::Random.AbstractRNG=Random.default_rng(),
                    mag_lim::Number = Inf,
                    mag_lim_name::String = "V",
                    binary_model::StarFormationHistories.AbstractBinaryModel =
                        StarFormationHistories.RandomBinaryPairs(0.3))
```

与えられた初期星質量 `mini_vec`、絶対等級 `mags`、およびフィルタ名 `mag_names` に基づいて、総人口誕生星質量 `limit`（例：1e5 太陽質量）で定義された等時線からの星のランダムサンプルを生成します。初期星質量は提供された `imf` からサンプリングされます。

# 引数

  * `mini_vec::AbstractVector{<:Number}` は、等時線内の星の初期質量（太陽質量単位）を含みます。`Interpolations.deduplicate_knots!(mini_vec)` を呼び出すため、可変でなければなりません。
  * `mags` は、`mini_vec` で提供された同じ星に対応する、希望するフィルタの等時線からの絶対等級を含みます。`mags` は内部的に解釈され、[`StarFormationHistories.ingest_mags`](@ref) によって標準形式に変換されます。有効な入力は次のとおりです：

      * `mags::AbstractVector{AbstractVector{<:Number}}` の場合、外側のベクトルの長さ `length(mags)` は `length(mini_vec)` と等しくすることができ、内側のベクトルの長さは提供するフィルタの数とすべて等しくなければなりません。または、外側のベクトルの長さは提供するフィルタの数と等しく、内側のベクトルの長さはすべて `length(mini_vec)` と等しくなければなりません。これはより一般的な使用ケースです。
      * `mags::AbstractMatrix{<:Number}` の場合、`mags` は2次元でなければなりません。有効な形状は `size(mags) == (length(mini_vec), nfilters)` または `size(mags) == (nfilters, length(mini_vec))` であり、`nfilters` は提供するフィルタの数です。
  * `mag_names::AbstractVector{String}` は、`mags` で提供するフィルタを説明する文字列を含みます。例としては `["B","V"]` などがあります。これらは、`mag_lim` が有限である場合に、返される最も暗い星を制限するために使用されます。
  * `limit::Number` は、サンプリングしたい人口の総誕生星質量を示します。人口質量に関する詳細は「ノート」セクションを参照してください。
  * `imf::Distributions.Sampleable{Distributions.Univariate, Distributions.Continuous}` は、質量をサンプリングするために使用する `rand(rng::Random.AbstractRNG, imf)` メソッドを持つ、サンプリング可能な連続単変量分布で、星の初期質量関数を実装しています。すべての `Distributions.ContinuousUnivariateDistribution` のインスタンスも有効です。一般的に使用されるIMFの実装は [InitialMassFunctions.jl](https://github.com/cgarling/InitialMassFunctions.jl) で入手できます。

# キーワード引数

  * `dist_mod::Number=0` は、特定の距離での人口をシミュレートするために返される等級に追加したい距離モジュラスです（[`StarFormationHistories.distance_modulus`](@ref) を参照）。
  * `rng::Random.AbstractRNG=Random.default_rng()` は、`imf` から初期星質量をサンプリングするために使用されるrngインスタンスです。
  * `mag_lim::Number=Inf` は、出力で返される星の最も暗い見かけの等級を示します。この等級よりも暗い星はサンプリングされ、人口の総質量に適切に寄与しますが、返されることはありません。
  * `mag_lim_name::String="V"` は、星が `mag_lim` よりも暗いかどうかを考慮する際に使用するフィルタ名（`mag_names` に含まれる）を示します。`mag_lim` が無限の場合は使用されません。
  * `binary_model::StarFormationHistories.AbstractBinaryModel=StarFormationHistories.RandomBinaryPairs(0.3)` は、バイナリを扱うためのモデルのインスタンスです。現在提供されているオプションは [`NoBinaries`](@ref)、[`RandomBinaryPairs`](@ref)、および [`BinaryMassRatio`](@ref) です。

# 戻り値

`(sampled_masses, sampled_mags)` は次のように定義されます。

  * `sampled_masses::Vector{SVector{N,eltype(imf)}}` は、[`sample_system`](@ref) によってサンプリングされた星の初期質量を含むベクトルです。形式の詳細については、そのメソッドのドキュメントを参照してください。簡単に言えば、各 `StaticArrays.SVector` は1つの星系を表し、各 `StaticArrays.SVector` の各エントリはその星系内の1つの星です。伴侶がサンプリングされる可能性があった場合はエントリが0になります（すなわち、マルチスターシステムをサポートする `binary_model` を使用している場合）。
  * `sampled_mags::Vector{SVector{N,<:Number}}` は、サンプリングされた星のマルチバンド等級を持つ `StaticArrays.SVectors` を含むベクトルです。バンド `j` における星 `i` の等級を取得するには、`sampled_mags[i][j]` とインデックスします。これは、`reduce(hcat,sampled_mags)` を使用して2次元の `Matrix` として再解釈できます。

# ノート

## 人口質量

特定の等時線と初期質量ベクトル `mini_vec` が与えられた場合、現在までに死んだ星は等時線に含まれないため、星の誕生質量の全範囲をカバーすることは決してありません。しかし、これらの星は*生まれた*ものであり、システムの総誕生質量に寄与します。サンプリング時にこの失われた質量を適切に考慮する方法は2つあります。

1. `imf` 分布からサンプリングできる質量の上限を、星の最大誕生質量の物理的な値（例：100太陽質量）に設定します。この場合、これらの星は `imf` からサンプリングされ、その質量はシステムに寄与しますが、誕生質量が `maximum(mini_vec)` より大きい場合は返されません。これは通常、ユーザーにとって最も簡単で、10 Gyr 等時線の場合は効率の約15%の損失にしかなりません。このアプローチは、バイナリをサンプリングする際に推奨されます。
2. `imf` 分布からサンプリングできる質量の上限を `maximum(mini_vec)` に設定し、より高い質量の星をサンプリングしないことによって失われた初期星質量の量を考慮して `limit` を調整します。これは次のように計算できます：`new_limit = limit * ( QuadGK.quadgk(x->x*pdf(imf,x), minimum(mini_vec), maximum(mini_vec))[1] / QuadGK.quadgk(x->x*pdf(imf,x), minimum(imf), maximum(imf))[1] )`。乗数因子は、初期質量が `minimum(mini_vec)` と `maximum(mini_vec)` の間にある星に含まれる人口星質量の割合です。この因子は次の比率です。

$$
\frac{\int_a^b \ m \times \frac{dN(m)}{dm} \ dm}{\int_0^∞ \ m \times \frac{dN(m)}{dm} \ dm}.
$$

バイナリが含まれる場合、このアプローチは `maximum(mini_vec)` よりも質量が小さい星の間でのみバイナリペアを形成します。これは望ましくない可能性が高いため、バイナリを含める際には前のアプローチを推奨します。 ```

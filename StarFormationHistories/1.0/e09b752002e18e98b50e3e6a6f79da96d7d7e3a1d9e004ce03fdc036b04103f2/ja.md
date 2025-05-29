```
(sampled_masses, sampled_mags) = generate_stars_mass_composite(mini_vec::AbstractVector{<:AbstractVector{<:Number}}, mags::AbstractVector, mag_names::AbstractVector{String}, limit::Number, massfrac::AbstractVector{<:Number}, imf::Sampleable{Univariate,Continuous}; kws...)
```

複数の等時線を使用して複雑な星形成履歴を持つ星のランダムサンプルを生成します。 [`generate_stars_mass`](@ref) と非常に似ていますが、等時線に関連する引数 `mini_vec` と `mags` は、考慮すべき等時線の全セットに関連するデータを含むベクトルのベクトルである必要があります。サンプル集団の総誕生星質量は `limit` で与えられます。この質量の各個別の等時線に割り当てられる割合は `massfrac` ベクトルのエントリによって与えられます。これは基本的に `limit` を `massfrac` に従って比例配分し、各個別の星集団に対して [`generate_stars_mass`](@ref) を呼び出します。そのため、複数の星集団にわたってマルチスレッドで設定されています。

# 引数

  * `mini_vec::AbstractVector{<:AbstractVector{<:Number}}` は、各等時線の星の初期質量（太陽質量単位）を含みます。内部ベクトルは可変である必要があります。なぜなら、各ベクトルに対して `Interpolations.deduplicate_knots!` を呼び出すからです。 `mini_vec` の長さは等時線の数と等しくする必要があります。
  * `mags` は、`mini_vec` に提供された同じ星に対応する希望するフィルターの等時線からの絶対等級を含みます。 `mags` の長さは等時線の数と等しくする必要があります。 `mags` の各要素は、内部的に解釈され、[`StarFormationHistories.ingest_mags`](@ref) によって標準形式に変換されます。 `mags` の各要素の有効な形式は次のとおりです：

      * `AbstractVector{AbstractVector{<:Number}}` の場合、ベクトルの長さ `length(mags[i])` は `length(mini_vec[i])` と等しくすることができ、内側のベクトルの長さは提供するフィルターの数と等しくなければなりません。または、外側のベクトルの長さが提供するフィルターの数と等しく、内側のベクトルの長さはすべて `length(mini_vec[i])` と等しくなければなりません。これはより一般的な使用ケースです。
      * `AbstractMatrix{<:Number}` の場合、`mags[i]` は2次元でなければなりません。有効な形状は `size(mags[i]) == (length(mini_vec[i]), nfilters)` または `size(mags[i]) == (nfilters, length(mini_vec[i]))` であり、`nfilters` は提供するフィルターの数です。
  * `mag_names::AbstractVector{String}` は、`mags` で提供するフィルターを説明する文字列を含みます。例としては `["B","V"]` などがあります。これらは、`mag_lim` が有限である場合に、返される最も暗い星を制限するために使用するフィルターを決定するために使用されます。これらはすべての等時線に対して同じであると仮定されます。
  * `limit::Number` は、サンプルしたい集団の総誕生星質量を与えます。
  * `massfrac::AbstractVector{<:Number}` は、各個別の星集団に割り当てられる質量の相対的な割合を与えるベクトルです。長さは `mini_vec` と `mags` の長さと等しくなければなりません。
  * `imf::Distributions.Sampleable{Distributions.Univariate, Distributions.Continuous}` は、質量をサンプリングするために使用する `rand(rng::Random.AbstractRNG, imf)` メソッドを持つ、定義された星の初期質量関数を実装するサンプル可能な連続単変量分布です。 `Distributions.ContinuousUnivariateDistribution` のすべてのインスタンスも有効です。一般的に使用されるIMFの実装は [InitialMassFunctions.jl](https://github.com/cgarling/InitialMassFunctions.jl) で入手できます。

# キーワード引数

すべてのキーワード引数 `kws...` は [`generate_stars_mass`](@ref) に渡されます。詳細については、そのメソッドのドキュメントを参照してください。

# 戻り値

  * `sampled_masses::Vector{Vector{SVector{N,eltype(imf)}}}` は、サンプルされた星の初期星質量を含むベクトルのベクトルです。外側のベクトルは、星が生成された等時線によって区切られています。すなわち、すべての `sampled_masses[1]` は `mini_vec[1]` からサンプルされ、以下同様です。これらは `reduce(vcat,sampled_masses)` を使用して単一のベクトルに連結できます。含まれる `StaticArrays.SVector` の形式は、[`sample_system`](@ref) からの出力と同様です。詳細については、そのメソッドのドキュメントを参照してください。
  * `sampled_mags::Vector{Vector{SVector{N,<:Number}}}` は、サンプルされた星のマルチバンド等級を持つ `StaticArrays.SVectors` を含むベクトルのベクトルです。外側のベクトルは、星が生成された等時線によって区切られています。すなわち、すべての `sampled_mags[1]` は `mags[1]` からサンプルされ、以下同様です。等時線 `k` からサンプルされたバンド `j` の星 `i` の等級を取得するには、`sampled_mags[k][i][j]` を使用します。これを `reduce(vcat,sampled_mags)` で `Vector{SVector}` に連結し、`reduce(hcat,reduce(vcat,sampled_mags))` で2次元の `Matrix` に連結できます。

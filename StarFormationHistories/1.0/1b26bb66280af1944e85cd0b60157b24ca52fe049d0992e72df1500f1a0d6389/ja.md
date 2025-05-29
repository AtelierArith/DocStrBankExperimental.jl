```
(sampled_masses, sampled_mags) = generate_stars_mag_composite(mini_vec::AbstractVector{<:AbstractVector{<:Number}}, mags::AbstractVector, mag_names::AbstractVector{String}, absmag::Number, absmag_name::String, fracs::AbstractVector{<:Number}, imf::Sampleable{Univariate,Continuous}; frac_type::String="lum", kws...)
```

複数の等時線を使用して複雑な星形成履歴を持つ星のランダムサンプルを生成します。 [`generate_stars_mag`](@ref)と非常に似ていますが、等時線に関連する引数`mini_vec`と`mags`は、考慮される等時線のフルセットに関連するデータを含むベクトルのベクトルである必要があります。サンプルされた集団の総絶対等級は`absmag`によって与えられます。各個別の等時線に割り当てられる光度の割合は`frac`ベクトルのエントリによって与えられます。これは基本的に`frac`に従って光度を比例配分し、各個別の星の集団に対して[`generate_stars_mag`](@ref)を呼び出します。そのため、複数の星の集団にわたってマルチスレッドで設定されています。

# 引数

  * `mini_vec::AbstractVector{<:AbstractVector{<:Number}}`は、各等時線の星の初期質量（太陽質量単位）を含みます。内部ベクトルは可変である必要があります。なぜなら、各ベクトルに対して`Interpolations.deduplicate_knots!`を呼び出すからです。`mini_vec`の長さは等時線の数と等しくする必要があります。
  * `mags`は、`mini_vec`で提供された同じ星に対応する等時線からの絶対等級を含みます。`mags`の長さは等時線の数と等しくする必要があります。`mags`の各要素は、内部的に解釈され、[`StarFormationHistories.ingest_mags`](@ref)によって標準形式に変換されます。`mags`の個々の要素の有効な形式は次のとおりです：

      * `AbstractVector{AbstractVector{<:Number}}`の場合、ベクトルの長さ`length(mags[i])`は`length(mini_vec[i])`と等しくすることができ、その場合、内部ベクトルの長さは提供するフィルターの数と等しくなければなりません。または、外部ベクトルの長さが提供するフィルターの数と等しく、内部ベクトルの長さはすべて`length(mini_vec[i])`と等しくなければなりません。これはより一般的な使用ケースです。
      * `AbstractMatrix{<:Number}`の場合、`mags[i]`は2次元でなければなりません。有効な形状は`size(mags[i]) == (length(mini_vec[i]), nfilters)`または`size(mags[i]) == (nfilters, length(mini_vec[i]))`であり、`nfilters`は提供するフィルターの数です。
  * `mag_names::AbstractVector{String}`は、`mags`で提供するフィルターを説明する文字列を含みます。例としては`["B","V"]`があります。これらは、`mag_lim`が有限である場合に、返される最も暗い星を制限するために使用するフィルターを決定するために使用されます。これらはすべての等時線に対して同じであると仮定されます。
  * `absmag::Number`は、サンプルされる複雑な集団の総絶対等級を与えます。
  * `fracs::AbstractVector{<:Number}`は、各個別の星の集団に割り当てられる光度または質量の相対的な割合（`frac_type`キーワード引数によって決定される）を与えるベクトルです。長さは`mini_vec`と`mags`の長さと等しくする必要があります。
  * `imf::Distributions.Sampleable{Distributions.Univariate, Distributions.Continuous}`は、質量をサンプリングするために使用する`rand(rng::Random.AbstractRNG, imf)`メソッドを定義した星の初期質量関数を実装するサンプル可能な連続単変量分布です。`Distributions.ContinuousUnivariateDistribution`のすべてのインスタンスも有効です。一般的に使用されるIMFの実装は、[InitialMassFunctions.jl](https://github.com/cgarling/InitialMassFunctions.jl)で入手できます。

# キーワード引数

  * `frac_type::String`は、"lum"の場合、`fracs`は各個別の等時線の相対光度割合を含むと仮定され、"mass"の場合、`fracs`は質量割合を含むと仮定されます（"mass"はまだ実装されていません）。

他のすべてのキーワード引数`kws...`は[`generate_stars_mag`](@ref)に渡されます。詳細については、そのメソッドのドキュメントを参照してください。

# 戻り値

  * `sampled_masses::Vector{Vector{SVector{N,eltype(imf)}}}`は、サンプルされた星の初期質量を含むベクトルのベクトルです。外部ベクトルは、星が生成された等時線によって区切られています。つまり、すべての`sampled_masses[1]`は`mini_vec[1]`からサンプルされ、以下同様です。これらは`reduce(vcat,sampled_masses)`を使用して単一のベクトルに連結できます。含まれる`StaticArrays.SVector`の形式は、[`sample_system`](@ref)からの出力と同様です。詳細については、そのメソッドのドキュメントを参照してください。
  * `sampled_mags::Vector{Vector{SVector{N,<:Number}}}`は、サンプルされた星のマルチバンド等級を持つ`StaticArrays.SVectors`を含むベクトルのベクトルです。外部ベクトルは、星が生成された等時線によって区切られています。つまり、すべての`sampled_mags[1]`は`mags[1]`からサンプルされ、以下同様です。等時線`k`からサンプルされた星`i`のバンド`j`の等級を取得するには、`sampled_mags[k][i][j]`を使用します。これを`reduce(vcat,sampled_mags)`を使用して`Vector{SVector}`に連結し、`reduce(hcat,reduce(vcat,sampled_mags))`を使用して2次元の`Matrix`に連結できます。

```

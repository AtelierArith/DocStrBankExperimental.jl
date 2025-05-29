サンプル出力ファイルをStanSample.jlによって作成し、要求された`output_format`で返します。デフォルトのoutput_formatは:tableです。オプションでパラメータシンボルのリストを返すこともできます。

```julia
read_samples(model; ...)
read_samples(
    model,
    output_format;
    include_internals,
    return_parameters,
    chains,
    start,
    kwargs...
)

```

# 拡張ヘルプ

### 必須引数

```julia
* `model`                         : <: CmdStanModel
* `output_format=:table`          : サンプルの要求された形式
```

### オプション引数

```julia
* `include_internals=false`       : 内部Stanパラメータを含める
* `return_parameters=false`       : (output_format, parameter_symbols)のタプルを返す
* `chains=1:m.num_chains*m.num_cpp_chains` : 出力に含めるチェーン（フォークプロセス）
* `start=1`                       : 含める最初のサンプル
* `kwargs...`                     : その他のキーワード引数をキャプチャ
```

現在サポートされているoutput_formatsは次のとおりです：

1. :table (デフォルト: StanTable Tablesオブジェクト、すべてのチェーンが追加される)
2. :array (3次元配列形式 - [samples, parameters, chains])
3. :namedtuple (NamedTupleオブジェクト、すべてのチェーンが追加される)
4. :namedtuples (Vector{NamedTuple}オブジェクト、個別のチェーン)
5. :tables (Vector{Tables}オブジェクト、個別のチェーン)
6. :dataframe (DataFrames.DataFrameオブジェクト、すべてのチェーンが追加される)
7. :dataframes (Vector{DataFrames.DataFrame}オブジェクト、個別のチェーン)
8. :keyedarray (AxisDict.jlからのKeyedArrayオブジェクト)
9. :particles (Dict{MonteCarloMeasurements.Particles})
10. :mcmcchains (MCMCChains.Chainsオブジェクト)
11. :nesteddataframe (ベクトルと行列を持つDataFrame)

チェーンを読み込む別の方法は`inferencedata(model)`によって提供されます。テストディレクトリのtest_inferencedata.jlを参照してください。

基本的にチェーンはArray、KeyedArray、NamedTuple、StanTable、InferenceObject、DataFrame（ネストされた列を持つ可能性あり）、ParticlesまたはMCMCChains.Chainsオブジェクトとして返すことができます。

オプション8から10は、AxisKeys.jl、MonteCarloMeasurements.jlまたはMCMCChains.jlの存在によって有効になります。

NamedTuple、StanTableおよびDataFrameタイプの場合、すべてのチェーンを追加するか、各チェーンのためにVector{...}として返すことができます。

NamedTupleおよびDataFrame出力*形式の場合、列:treedepth__、:n*leapfrogs**および:divergent**はそれぞれInt、IntおよびBool型に変換されます。

オプションのキーワード引数`chains`を使用すると、チェーンのサブセットを含めることができます。例：`chains = [2, 4]`。

オプションのキーワード引数`start`は、削除すべきサンプルを指定します。例：ウォームアップサンプルの場合。

注意：

1. Stanの`thinning`オプションの使用は、startの値に干渉します。
2. Startは含まれる最初のサンプルです。例：1000のウォームアップサンプルがある場合、startは1001に設定する必要があります。

NamedTuple出力形式はパラメータベクトルを抽出して結合します。例：Stanのcmdstanが`a.1, a.2, a.3`を返す場合、NamedTupleは`a`のみを含みます。

KeyedArrayおよびStanTableオブジェクトの場合、オーバーロードされた`matrix()`メソッドを使用してパラメータのブロックを抽出できます：

```
stantable = read_samples(m10.4s, :table)
atable = matrix(stantable, "a")
```

追加されたDataFrameの場合、例えば`DataFrame(df, :log_lik)`を使用して変数のセットをブロックできます。この例では`log_lik.1, log_lik.2, etc.`です。

現在、:tableはデフォルトのチェーンoutput_format（StanTableオブジェクト）です。

一般的に、望ましいoutput_formatを指定する方が安全です。この領域はまだStanJuliaエコシステムで活発に開発されています。デフォルトは頻繁に変更されています！

# convert_a3d

cmdstanによって作成された出力ファイルを選択した形状に変換します。

### メソッド

```julia
convert_a3d(a3d_array, cnames, ::Val{Symbol})
```

### 必須引数

```julia
* `a3d_array::Array{Float64}(n_draws, n_variables, n_chains`      : cmdstanによって作成された出力ファイルから読み込みます                                   
* `cnames::Vector{AbstractString}`                                                 : 監視された変数名
```

### オプション引数

```julia
* `::Val{Symbol} = :array`                                                                             : 出力形式
```

呼び出されるメソッドは、stanmodelで定義されたoutput_formatに基づいています。例えば：

stanmodel = Stanmodel(num/*samples=1200, thin=2, name="bernoulli",     model=bernoullimodel, output*format=:array);

現在サポートされている形式は次のとおりです：

1. :array (a3d_array形式、CmdStanのデフォルト)
2. :namedarray (NamedArraysオブジェクト)
3. :dataframe (DataFramesオブジェクト)
4. :mambachains (Mamba.Chainsオブジェクト)
5. :mcmcchain (TuringLang/Chainsオブジェクト)

オプション3から5は、それぞれStanDataFrames、StanMamba、StanMCMCChainパッケージによって提供されます。

```

### 戻り値
```

julia

  * `res`                       : 指定された形式に変換されたサンプル。

```

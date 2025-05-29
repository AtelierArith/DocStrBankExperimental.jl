出力ファイルをcmdstanによって作成された形に変換します

```julia
convert_a3d(a3d_array, cnames, ; kwargs...)

```

### メソッド

```julia
convert_a3d(a3d_array, cnames; output_format=::Val{Symbol}, start=1)
```

### 必須引数

```julia
* `a3d_array::Array{Float64, 3},`      : cmdstanによって作成された出力ファイルから読み込みます                                   
* `cnames::Vector{AbstractString}`     : 監視された変数名
```

### オプション引数

```julia
* `::Val{Symbol}`                      : 出力形式、デフォルトは :mcmcchains
* `::start=1`                          : MCMCChains.Chainsの最初の描画
```

### 戻り値

```julia
* `res`                       : 指定された形式に変換された描画。
```

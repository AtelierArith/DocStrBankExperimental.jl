# quap

ポスタリオ分布の二次近似をDataFrameで

### 方法

```julia
quap(df) 
```

### 必要な引数

```julia
* `df::DataFrame`                      : サンプル（チェーン）から生成されたDataFrame
```

### 戻り値

```julia
* `result::NamedTuple`                 : 二次近似を表すNamedTuple
```

Dictに変換するには、次のようにします:

```julia
dct = Dict(pairs(result))
```

### 例

```julia
# SampleModelでstan_sample()を実行
if success(rc)
  
  df = read_samples(sm; output_format=:dataframe)
  q = quap(df)
end
```

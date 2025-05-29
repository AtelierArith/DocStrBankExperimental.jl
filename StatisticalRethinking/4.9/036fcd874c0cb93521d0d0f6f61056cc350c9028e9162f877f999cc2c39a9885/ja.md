# サンプル

DataFrameからのサンプル行

### メソッド

```julia
sample(df, n; replace, ordered) 
```

### 必須引数

```julia
* `df::DataFrame`                      : DataFrame
* `n::Int`                             : サンプル数
```

### オプション引数

```julia
* `rng::AbstractRNG`                   : 擬似乱数生成器
* `replace::Bool=true`                 : 置換ありでサンプリング
* `ordered::Bool=false`                : サンプルをソート
```

### 戻り値

```julia
* `result`                             : サンプルの配列
```

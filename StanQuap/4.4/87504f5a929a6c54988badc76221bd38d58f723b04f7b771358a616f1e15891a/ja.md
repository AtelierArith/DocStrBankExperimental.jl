事後分布の二次近似を計算します。

```julia
stan_quap(name, model; kwargs...)
```

### 必要な引数

```julia
* `name::String`                : SampleModelの名前
* `model::String`               : Stan言語モデル
```

### キーワード引数

```julia
* `data`                        : モデルのデータ (NamedTupleまたはDuct)
* `init`                        : パラメータの初期値 (NamedTupleまたはDict)
```

### 戻り値

```julia
* `res::QuapResult`              : 戻り値のオブジェクト
```

一般的に`init`を使用すると、より良い動作が得られます。

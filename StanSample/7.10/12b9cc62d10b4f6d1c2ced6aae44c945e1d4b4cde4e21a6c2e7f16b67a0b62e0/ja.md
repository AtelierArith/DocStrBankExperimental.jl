`name`_summary.csv ファイルを作成します。

```julia
stan_summary(m)
stan_summary(m, printsummary)

```

# 拡張ヘルプ

### 必須引数

```julia
* `model::SampleModel             : SampleModel
```

### オプションの位置引数

```julia
* `printsummary=false             : サマリーを表示
```

完了後、...*summary.csv ファイルが作成されました。このファイルは `df = read*summary(model))` によって DataFrame として読み込むことができます。

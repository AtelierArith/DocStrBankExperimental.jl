```
write_hparams!(logger::TBLogger, hparams::Dict{String, Any}, metrics::AbstractArray{String})
```

提供されたハイパーパラメータをロガーに書き込み、追跡すべきすべてのメトリックを記録します。

`hparams`の値は`String`、`Bool`、または`Real`のサブタイプである必要があります。すべての`Real`値は、ログを書き込む際に`Float64`に変換されます。

`metrics`は、ログに記録されたスカラーに対応するタグのリストである必要があります。Tensorboardは、自動的にこの値に使用するために最新のメトリックを抽出します。

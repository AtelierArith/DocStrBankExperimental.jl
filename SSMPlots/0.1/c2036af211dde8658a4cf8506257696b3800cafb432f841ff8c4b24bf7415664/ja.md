```
plot_model(model; 
    add_density=false, density_kwargs=(), n_sim=1, kwargs...)
```

連続多変量逐次サンプリングモデルの証拠蓄積プロセスをプロットします。

# 引数

  * `model::ContinuousMultivariateSSM`: 連続多変量逐次サンプリングモデル

# キーワード

  * `add_density=false`: 真の場合、閾値線の上に密度プロットを追加
  * `density_kwargs=()`: 密度プロットにオプションのキーワード引数を渡す
  * `labels = default_labels(model)`: パラメータラベルオプションのベクトル
  * `n_sim=1`: オプションごとのシミュレートされた意思決定プロセスの数
  * `kwargs...`: プロットオプションを設定するためのオプションのキーワード引数

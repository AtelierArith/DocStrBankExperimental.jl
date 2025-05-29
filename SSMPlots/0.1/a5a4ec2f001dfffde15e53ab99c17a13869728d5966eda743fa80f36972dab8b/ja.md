```
plot_model(model; 
    add_density=false, density_kwargs=(), n_sim=1, kwargs...)
```

一般的なSSMの証拠蓄積プロセスをプロットします。

# 引数

  * `model`: SSMを表す一般的なオブジェクト

# キーワード

  * `add_density=false`: trueの場合、閾値線の上に密度プロットを追加
  * `density_kwargs=()`: 密度プロットにオプションのキーワード引数を渡す
  * `labels = default_labels(model)`: パラメータラベルオプションのベクトル
  * `density_scale = compute_threshold(model)`: 密度の最大高さをスケール
  * `n_sim=1`: オプションごとのシミュレーションされた意思決定プロセスの数
  * `kwargs...`: プロットオプションを設定するためのオプションのキーワード引数

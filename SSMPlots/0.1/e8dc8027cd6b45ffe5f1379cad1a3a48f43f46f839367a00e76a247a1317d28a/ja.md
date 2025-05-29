```
plot!([cur_plot], d::ContinuousMultivariateSSM; t_range=default_range(d), kwargs...)
```

既存のプロットに多変量連続逐次サンプリングモデルの周辺確率密度を追加します

# 引数

  * `cur_plot`: オプションの現在のプロット
  * `d::ContinuousMultivariateSSM`: 多変量連続逐次サンプリングモデル

# キーワード

  * `t_range`: 確率密度がプロットされる時間点の範囲
  * `m_args=()`: 該当する場合に`rand`に渡されるオプションの位置引数
  * `kwargs...`: プロットオプションを設定するためのオプションのキーワード引数

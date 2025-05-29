```
plot(d::ContinuousMultivariateSSM; t_range=default_range(d), kwargs...)
```

N次元連続逐次サンプリングモデルの周辺確率密度をプロットします。

# 引数

  * `d::ContinuousMultivariateSSM`: N次元連続逐次サンプリングモデルのモデルオブジェクト。

# キーワード

  * `t_range`: 確率密度がプロットされる時間点の範囲
  * `m_args=()`: 該当する場合に`rand`に渡されるオプションの位置引数
  * `kwargs...`: プロットオプションを設定するためのオプションのキーワード引数

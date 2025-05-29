```
find_partitions(model, p_fun, options, args...; show_timer=false, kwargs...)
```

パラメータ空間の分割を実行します。

# 引数

  * `model`: パラメータのベクトルに基づいて予測を返すモデル関数
  * `p_fun`: 定性的データパターンを評価する関数
  * `options`: アルゴリズムを構成するためのオプションのセット
  * `args...`: `model` と `p_fun` に渡される引数

# キーワード

  * `show_timer=false`: true の場合、タイマーと進捗バーを表示します
  * `kwargs...`: `model` と `p_fun` に渡されるキーワード引数

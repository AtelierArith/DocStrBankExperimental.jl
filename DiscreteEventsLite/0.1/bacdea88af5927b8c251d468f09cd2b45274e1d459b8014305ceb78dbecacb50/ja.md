```
register!(scheduler, fun, when, t, args...; id="", description="", kwargs...)
```

スケジューラにイベントを追加するためのインターフェースです。

# 引数

  * `scheduler`: イベントスケジューラ
  * `fun`: 実行する関数
  * `when`: `fun`の実行タイミング。オプション: `at`, `now`, `every`, `after`
  * `t`: `when`に関連付けられた時間値
  * `args...`: `fun`のためのオプションの位置引数
  * `id`: オプションのID文字列
  * `description`: オプションの説明

# キーワード

  * `kwargs...`: `fun`のためのオプションのキーワード引数

```
BlockingScheduler(; clock=real_time_clock, delayfunc=_sleep, jobconfig=JobConfig())
```

`BlockingScheduler` は最もシンプルなスケジューラです。これは `AbstractScheduler` を実装しています。

これはジョブをスケジュールするための単一スレッド実装です。

# オプション引数

  * `clock::AbstractClock`: スケジューラによって使用される時計（デフォルトでは `real_time_clock` で、これはシステムのUTC時間ですが、シミュレーション目的で `SimClock` 構造体も渡すことができます）。
  * `delayfunc::DelayFunc`: 次のタスクが実行されるまで待機する責任を持つファンクタ（デフォルトでは `_sleep` が使用されますが、シミュレーション目的で `NoSleep` 構造体も渡すことができます）。
  * `jobconfig::JobConfig`: ジョブ設定のデフォルト設定（`misfire_grace_period`...）

```
BossOptions(; kwargs...)
```

BOSSアルゴリズムの雑多な設定を保存します。

# キーワード

  * `info::Bool`: `info=false`に設定すると、BOSSアルゴリズムの出力が抑制されます。
  * `debug::Bool`: `debug=true`に設定すると、キャッチされた最適化エラーのスタックトレースが表示されます。
  * `parallel_evals::Symbol`: 可能な値: `:serial`, `:parallel`, `:distributed`。デフォルトは`:parallel`です。       1つのバッチ内で複数の目的関数評価を直列、並列、または分散方式で実行するかどうかを決定します。       （AMのバッチ処理が使用されている場合にのみ影響があります。）
  * `callback::BossCallback`: 提供される場合、`callback(::BossProblem; kwargs...)`       はBO手続きが開始される前と各イテレーションの後に呼び出されます。

関連情報: [`bo!`](@ref)

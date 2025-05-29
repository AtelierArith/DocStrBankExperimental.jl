```
XPRSmsaddpreset(prob, description, preset, maxjobs, data)::prob
```

マルチスタートジョブプールにジョブのプリセットをロードします。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `description::Union{Nothing,AbstractString}`: プリセットのテキスト説明。
  * `preset::Integer`: ロードするプリセットの番号。
  * `maxjobs::Integer`: マルチスタートプールに追加される最大ジョブ数。
  * `data::Any`: マルチスタートコールバックに渡されるジョブ固有のユーザーコンテキストポインタ。

# 戻り値

  * `prob::XPRSprob`: 現在のSLP問題。

C APIの対応する関数[XPRSmsaddpreset](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSmsaddpreset.html)のドキュメントも参照してください。

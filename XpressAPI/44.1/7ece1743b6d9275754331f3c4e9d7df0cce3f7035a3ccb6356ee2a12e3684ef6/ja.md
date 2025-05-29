```
XPRSrepairweightedinfeasbounds(prob, lepref, gepref, lbpref, ubpref, lerelax, gerelax, lbrelax, ubrelax, phase2, delta, flags)::status
```

制約の緩和レベルを制限することを可能にする XPRSrepairweightedinfeas の拡張版です。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `lepref::AbstractVector{Number}`: 行の「以下」側を緩和するための好みを含むサイズ `ROWS` の配列。
  * `gepref::AbstractVector{Number}`: 行の「以上」側を緩和するための好みを含むサイズ `ROWS` の配列。
  * `lbpref::AbstractVector{Number}`: 下限を緩和するための好みを含むサイズ `COLS` の配列。
  * `ubpref::AbstractVector{Number}`: 上限を緩和するための好みを含むサイズ `COLS` の配列。
  * `lerelax::AbstractVector{Number}`: 行の「以下」側をどれだけ緩和できるかの上限を含むサイズ `ROWS` の配列。
  * `gerelax::AbstractVector{Number}`: 行の「以上」側をどれだけ緩和できるかの上限を含むサイズ `ROWS` の配列。
  * `lbrelax::AbstractVector{Number}`: 下限をどれだけ緩和できるかの上限を含むサイズ `COLS` の配列。
  * `ubrelax::AbstractVector{Number}`: 上限をどれだけ緩和できるかの上限を含むサイズ `COLS` の配列。
  * `phase2::Integer`: 最適化の第2フェーズを制御します：元の問題の目的感を使用する（デフォルト）；元の目的を使用して緩和された問題を最大化する；元の目的に関する最適化をスキップする；元の目的を使用して緩和された問題を最小化する；緩和が不可能な場合、問題の分析のために縮小不可能な不可能部分集合を生成する；緩和が不可能な場合、問題の分析のためにすべての縮小不可能な不可能部分集合を生成する。
  * `delta::Float64`: 第2フェーズの緩和乗数 -1。
  * `flags::Union{Nothing,AbstractString}`: オプティマイザに渡すフラグを指定します。

# 戻り値

  * `status::Int32`: 緩和後のステータス：1緩和された問題は不可能；2緩和された問題は無限大；3元の目的に関する緩和された問題の解は最適でない；4エラー（戻りコードが非ゼロの場合）；5数値的不安定性；6不可能な緩和の分析が行われたが、緩和は可能である。

C API の対応する関数 [XPRSrepairweightedinfeasbounds](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSrepairweightedinfeasbounds.html) のドキュメントも参照してください。

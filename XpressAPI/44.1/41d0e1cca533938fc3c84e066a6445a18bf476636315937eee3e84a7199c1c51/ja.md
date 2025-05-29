```
XPRSrepairweightedinfeas(prob, lepref, gepref, lbpref, ubpref, phase2, delta, flags)::status
```

不 feasibleな問題の選択された制約と境界を緩和することによって、選択された制約と境界を最小限に違反する「解」を特定しようとしますが、他のすべての制約と境界は満たします。

そのような解候補の中から、元の目的関数に関して最適なものを選択します。コンソール版については、REPAIRINFEASを参照してください。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `lepref::AbstractVector{Number}`: 行の小さいまたは等しい側を緩和するための好みを含むサイズ`ROWS`の配列。
  * `gepref::AbstractVector{Number}`: 行の大きいまたは等しい側を緩和するための好みを含むサイズ`ROWS`の配列。
  * `lbpref::AbstractVector{Number}`: 下限を緩和するための好みを含むサイズ`COLS`の配列。
  * `ubpref::AbstractVector{Number}`: 上限を緩和するための好みを含むサイズ`COLS`の配列。
  * `phase2::Integer`: 最適化の第2段階を制御します：元の問題の目的の感覚を使用する（デフォルト）；元の目的を使用して緩和された問題を最大化する；元の目的に関する最適化をスキップする；元の目的を使用して緩和された問題を最小化する；緩和が不 feasibleな場合、問題の分析のために不可約不 feasible部分集合を生成する；緩和が不 feasibleな場合、問題の分析のためにすべての不可約不 feasible部分集合を生成する。
  * `delta::Float64`: 第2段階の緩和乗数 -1。
  * `flags::Union{Nothing,AbstractString}`: Optimizerに渡すフラグを指定します。

# 戻り値

  * `status::Int32`: 緩和後のステータス：1緩和された問題は不 feasible；2緩和された問題は無限大；3元の目的に関して緩和された問題の解は非最適；4エラー（戻りコードが非ゼロの場合）；5数値的不安定性；6不 feasibleな緩和の分析が行われましたが、緩和は feasibleです。

C APIの対応する関数[XPRSrepairweightedinfeas](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSrepairweightedinfeas.html)のドキュメントも参照してください。

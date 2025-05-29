```
XPRSmsaddcustompreset(prob, description, preset, maxjobs, ninitial, colind, initial, nintcontrols, intcontrolid, intcontrolval, ndblcontrols, dblcontrolid, dblcontrolval, data)::prob
```

XSLPmsaddjobとXSLPmsaddpresetの組み合わせバージョンです。

記述されたプリセットが読み込まれ、提供された特定の設定で補充されます。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `description::Union{Nothing,AbstractString}`: ジョブのテキスト説明。
  * `preset::Integer`: 読み込むプリセット。
  * `maxjobs::Integer`: マルチスタートプールに追加する最大ジョブ数。
  * `ninitial::Integer`: 設定する初期値の数。
  * `colind::AbstractVector{Integer}`: 初期値を設定する変数のインデックス。
  * `initial::AbstractVector{Number}`: 初期値を設定する変数の初期値。
  * `nintcontrols::Integer`: 設定する整数制御の数。
  * `intcontrolid::AbstractVector{Integer}`: 設定する整数制御のインデックス。
  * `intcontrolval::AbstractVector{Integer}`: 設定する整数制御の値。
  * `ndblcontrols::Integer`: 設定する倍精度制御の数。
  * `dblcontrolid::AbstractVector{Integer}`: 設定する倍精度制御のインデックス。
  * `dblcontrolval::AbstractVector{Number}`: 設定する倍精度制御の値。
  * `data::Any`: マルチスタートコールバックに渡されるジョブ固有のユーザーコンテキストポインタ。

# 戻り値

  * `prob::XPRSprob`: 現在のSLP問題。

C APIの対応する関数[XPRSmsaddcustompreset](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSmsaddcustompreset.html)のドキュメントも参照してください。

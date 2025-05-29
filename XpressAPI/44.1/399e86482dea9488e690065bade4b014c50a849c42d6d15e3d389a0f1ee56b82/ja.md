```
XPRSiiswrite(prob, iis, filename, filetype, flags)::prob
```

与えられた不可約非可行集合 (IIS) を含む LP/MPS/CSV ファイルを書き込みます。

IIS 番号パラメータに 0 が渡されると、初期の非可行サブプロブレムが書き込まれます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `iis::Integer`: 書き込む IIS の順序番号。
  * `filename::Union{Nothing,AbstractString}`: 作成されるファイルの名前。
  * `filetype::Integer`: 作成されるファイルのタイプ: 0 は IIS を線形計画問題として含む lp/mps ファイルを作成し、1 は与えられた IIS に関する説明と補足情報を含むカンマ区切り (csv) ファイルを作成します。
  * `flags::Union{Nothing,AbstractString}`: XPRSwriteprob 関数に渡されるフラグ。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C API の対応する関数 [XPRSiiswrite](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSiiswrite.html) のドキュメントも参照してください。

```
XPRSwriteslxsol(prob, filename, flags)::prob
```

ASCIIソリューションファイル（`.slx`）をMPSファイルに似た形式で作成します。

これらのファイルは、XPRSreadslxsol関数を使用してOptimizerに再度読み込むことができます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `filename::Union{Nothing,AbstractString}`: ソリューションを書き込むファイル名を含む、最大MAXPROBNAMELENGTH文字の文字列。
  * `flags::Union{Nothing,AbstractString}`: `XPRSwriteslxsol`に渡すフラグ（`WRITESLXSOL`）：MIP問題の場合はLPソリューションを書き込む; MIPソリューションを書き込む; 数値値に対して完全精度を使用する（これは現在のデフォルト動作として廃止されました）; スラック変数を含む; dLPソリューションのみ：双対変数を含む; rLPソリューションのみ：削減コストを含む; 提供されたファイル名をそのまま使用し、`.slx`拡張子を追加しない; 出力ファイルを圧縮する。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSwriteslxsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSwriteslxsol.html)のドキュメントも参照してください。

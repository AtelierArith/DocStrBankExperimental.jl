```
XPRSreadslxsol(prob, filename, flags)::prob
```

XPRSwriteslxsol関数によって作成されたASCIIソリューションファイル`.slx`を読み込みます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `filename::Union{Nothing,AbstractString}`: ソリューションを読み込むファイル名を含む、最大MAXPROBNAMELENGTH文字の文字列。
  * `flags::Union{Nothing,AbstractString}`: `XPRSreadslxsol`に渡すフラグ（`READSLXSOL`）：非改行空白の変換；MIP問題の場合はLPソリューションとしてソリューションを読み込む；MIP問題のソリューションとしてソリューションを読み込む；`.slx`ファイルから複数のMIPソリューションを読み込み、それらをMIP問題に追加する；提供されたファイル名をそのまま使用し、`.slx`拡張子を追加しない；圧縮された入力ファイルを読み込む。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSreadslxsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSreadslxsol.html)のドキュメントも参照してください。

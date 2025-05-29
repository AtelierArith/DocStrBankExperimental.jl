```
XPRSreadbinsol(prob, filename, flags)::prob
```

バイナリソリューションファイルからソリューションを読み込みます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `filename::Union{Nothing,AbstractString}`: ソリューションを読み込むファイル名を含む、最大MAXPROBNAMELENGTH文字の文字列。
  * `flags::Union{Nothing,AbstractString}`: `XPRSreadbinsol`に渡すフラグ（`READBINSOL`）：MIPのソリューションとしてソリューションをmloadする; LPのソリューションとしてソリューションをxloadする; 提供されたファイル名をそのままvuseする（`.sol`拡張子を追加しない）; 圧縮された入力ファイルをzreadする。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数のドキュメント[XPRSreadbinsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSreadbinsol.html)も参照してください。

```
XPRSwritebinsol(prob, filename, flags)::prob
```

現在のMIPまたはLPソリューションを、後でオプティマイザに入力するためのバイナリソリューションファイルに書き込みます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `filename::Union{Nothing,AbstractString}`: ソリューションを書き込むファイル名を含む、最大MAXPROBNAMELENGTH文字の文字列。
  * `flags::Union{Nothing,AbstractString}`: `XPRSwritebinsol`に渡すフラグ（`WRITEBINSOL`）：moutput MIPソリューション; xoutput LPソリューション; vuse 提供されたファイル名をそのまま使用し、`.sol`拡張子を追加しない; zcompress 出力ファイルを圧縮する。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数のドキュメントも参照してください [XPRSwritebinsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSwritebinsol.html)。

```
XPRSreadbasis(prob, filename, flags)::prob
```

オプティマイザに、ファイルから以前に保存された基準を読み込むよう指示します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `filename::Union{Nothing,AbstractString}`: 基準を読み込むファイル名を含む、最大MAXPROBNAMELENGTH文字の文字列。
  * `flags::Union{Nothing,AbstractString}`: `XPRSreadbasis`に渡すフラグ（`READBASIS`）：CPLEX互換性;（効果はないが、互換性のために保持）; ninput 基準ファイルに基本的な解の値を含む; tinput 基準のコンパクトな高度な形式; v提供されたファイル名をそのまま使用し、`.bss`拡張子を追加しない; z圧縮された入力ファイルを読み込む。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSreadbasis](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSreadbasis.html) のドキュメントも参照してください。

```
XPRSwriteprtsol(prob, filename, flags)::prob
```

現在の解を固定形式のASCIIファイル、problem_name `.prt` に書き込みます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `filename::Union{Nothing,AbstractString}`: 解を書き込むファイル名を含む、最大MAXPROBNAMELENGTH文字の文字列。
  * `flags::Union{Nothing,AbstractString}`: `XPRSwriteprtsol`（`WRITEPRTSOL`）のフラグは次のとおりです：ファイルに書き込むのではなく、画面に解を表示する（メッセージコールバックを介して）；現在のMIP解の代わりにLP解を出力する；提供されたファイル名をそのまま使用し、`.prt`拡張子を追加しない；圧縮出力ファイルを書き込む；古典的感度分析を含める。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数のドキュメントも参照してください [XPRSwriteprtsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSwriteprtsol.html)。

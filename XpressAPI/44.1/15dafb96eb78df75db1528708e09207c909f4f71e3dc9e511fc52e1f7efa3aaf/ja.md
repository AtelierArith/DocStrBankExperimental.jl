```
XPRSwriteprob(prob, filename, flags)::prob
```

現在の問題をMPSまたはLPファイルに書き込みます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `filename::Union{Nothing,AbstractString}`: 問題を書き込むファイル名を含む最大MAXPROBNAMELENGTH文字の文字列。
  * `flags::Union{Nothing,AbstractString}`: フラグで、以下のいずれかまたは複数を指定できます: CPLEXと互換性のある形式で出力; 一行に一要素; スケーリングされた問題を出力; シャッフルされたベクトル名; LP形式で出力; 完全精度で値を出力（これは現在のデフォルト動作として廃止されています）; LP形式でXpressヘッダーを省略; 提供されたファイル名をそのまま使用し、`.mps`または`.lp`拡張子を追加しない; 出力ファイルを圧縮。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数のドキュメントも参照してください [XPRSwriteprob](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSwriteprob.html)。

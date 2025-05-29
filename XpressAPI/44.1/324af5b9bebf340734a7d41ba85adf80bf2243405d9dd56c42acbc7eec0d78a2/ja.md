```
XPRSwritesol(prob, filename, flags)::prob
```

現在の解をCSV形式のASCIIファイル、problem_name`.asc`（および`.hdr`）に書き込みます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `filename::Union{Nothing,AbstractString}`: 解を書き込むファイル名を含む、最大MAXPROBNAMELENGTH文字の文字列。
  * `flags::Union{Nothing,AbstractString}`: 出力されるオプションフィールドを制御するフラグ：sシーケンス番号; n名前; tタイプ; bbasis ステータス; aアクティビティ; cコスト（列）、スラック（行）; llower bound; uupper bound; ddj（列; 削減コスト）、デュアル値（行; シャドウ価格）; r右辺（行）。フラグが指定されていない場合、すべてのフィールドが出力されます。追加のフラグ：p完全精度で出力; q非ゼロ最適値を持つベクトルのみを出力; x現在のLP解をMIP解の代わりに出力; z出力ファイルを圧縮します。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSwritesol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSwritesol.html)のドキュメントも参照してください。

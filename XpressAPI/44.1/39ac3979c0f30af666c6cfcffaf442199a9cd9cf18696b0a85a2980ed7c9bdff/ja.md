```
XPRSwritebasis(prob, filename, flags)::prob
```

現在の基準をファイルに書き込み、後でオプティマイザに入力できるようにします。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `filename::Union{Nothing,AbstractString}`: 基準が書き込まれるファイル名を含む、最大MAXPROBNAMELENGTH文字の文字列。
  * `flags::Union{Nothing,AbstractString}`: `XPRSwritebasis`に渡すフラグ（`WRITEBASIS`）：スクランブルされたベクタ名；16進数での出力値；CPLEXと互換性のある形式での出力；内部の前処理された基準を出力；基準のコンパクトな高度な形式を出力；現在の解の値を含む基準ファイルを出力；単精度での値を出力；完全精度での値を出力（これは現在のデフォルト動作のため廃止予定）；提供されたファイル名をそのまま使用し、`.bss`拡張子を追加しない；出力ファイルを圧縮。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

対応する関数のドキュメントも参照してください [XPRSwritebasis](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSwritebasis.html) C APIにおいて。

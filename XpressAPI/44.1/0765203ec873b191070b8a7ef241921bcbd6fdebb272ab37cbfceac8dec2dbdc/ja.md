```
XPRSrestore(prob, probname, flags)::prob
```

XPRSsave (SAVE) によって作成されたファイルからオプティマイザのデータ構造を復元します。

最適化は、ファイルが作成された時点から再開できます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `probname::Union{Nothing,AbstractString}`: 問題名を含む最大 MAXPROBNAMELENGTH 文字の文字列。
  * `flags::Union{Nothing,AbstractString}`: 追加のフラグ force（効果なし、互換性のために保持）；hファイルからハードウェア情報を復元しない；v提供されたファイル名をそのまま使用し、`.svf` 拡張子を追加しない。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C API の対応する関数 [XPRSrestore](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSrestore.html) のドキュメントも参照してください。

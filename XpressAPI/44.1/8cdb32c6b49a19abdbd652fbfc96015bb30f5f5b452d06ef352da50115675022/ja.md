```
XPRS_PREPROBING
```

前処理: 前処理中にバイナリ変数に対して実行するプロービングの量。(整数)

これは、バイナリをその各値に固定し、その影響を分析することによって行われます。

デフォルト値: `-1`

値: -1 : 最適化ツールにプロービングの量を決定させる。 0 : 無効。 +1 : 軽いプロービング、少数の影響のみが検査される。 +2 : 完全なプロービング、すべてのバイナリに対してすべての影響が検査される。 +3 : 完全なプロービングを行い、問題が大幅に削減される限り繰り返す。

```
ICN(; nvars, dom_size, param, transformation, arithmetic, aggregation, comparison)
```

解釈可能な合成ネットワークを構築します。引数は以下の通りです：

  * `nvars`: 制約内の変数の数
  * `dom_size`: 制約内の任意の変数の最大ドメインサイズ
  * `param`: オプションのパラメータ（デフォルトは `nothing`）
  * `transformation`: 変換層（オプション）
  * `arithmetic`: 算術層（オプション）
  * `aggregation`: 集約層（オプション）
  * `comparison`: 比較層（オプション）

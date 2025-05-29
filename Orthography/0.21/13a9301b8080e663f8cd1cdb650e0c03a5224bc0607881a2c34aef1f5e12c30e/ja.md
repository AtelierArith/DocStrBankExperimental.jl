トークンレベルで引用可能な `CitableTextCorpus` を作成します。オプションのパラメータにより、指定されたトークンタイプ `filterby` によって結果のコーパスをフィルタリングしたり、トークンの正規化のために適用する関数 `normalizer` を指定したりできます（例：大文字小文字やアクセントの正規化）。

```julia
tokenizedcorpus(v; filterby, normalizer)

```

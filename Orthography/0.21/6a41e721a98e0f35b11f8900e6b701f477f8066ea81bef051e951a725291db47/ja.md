トークンレベルで引用可能な `CitableTextCorpus` を作成します。オプションのパラメータを使用すると、指定されたタイプのトークンのみを含めるように結果をフィルタリングし、カウントする前にトークンのテキスト値を正規化できます。

```julia
tokenizedcorpus(c, orthography; filterby, normalizer)

```

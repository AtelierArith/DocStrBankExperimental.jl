```
translate(model::AbstractLLM, description::AbstractString; interactive::Bool = false)
```

最適化問題の自然言語の `description` を、大規模言語モデル `model` に問い合わせることによって制約プログラミングモデルに翻訳します。`interactive` が真の場合、ユーザーはコマンドラインを通じてLLMの中間出力を確認し、必要に応じてそれらを修正するように促されます。

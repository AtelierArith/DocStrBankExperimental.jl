```julia
FrequentistRegression(::Symbol, model, formula, link = GLM.IdentityLink)
```

`FrequentistRegression`のコンストラクタ。`model`は任意の回帰モデルを指定できます。`fit`関数によって頻度主義回帰モデルコンテナを返すために使用されます。

```
(dfw::DiffFW)(θ::AbstractArray, frank_wolfe_kwargs::NamedTuple)
```

`θ`に対して、名前付きタプル`frank_wolfe_kwargs`で定義された設定を用いてフランク・ウルフアルゴリズムを適用します（位置引数として与えられます）。

解`x`と、追加情報を含む名前付きタプル`stats`のペアを返します（その内容は公開APIではカバーされておらず、主にデバッグに役立ちます）。

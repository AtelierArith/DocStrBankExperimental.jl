```
ESCFRSolver(game::Game; method::Symbol=:vanilla, alpha::Float64 = 1.0, beta::Float64 = 1.0, gamma::Float64 = 1.0, d::Int)
```

外部サンプリングCFRソルバーをいくつかの`game`でインスタンス化します。

単一のツリー探索のためにすべてのプレイヤーから単一のアクションをサンプリングします。探索を完了するのにかかる時間はO(|𝒜ᵢ|ᵈ)であり、ここでdはゲームの深さ、|𝒜ᵢ|は行動プレイヤーのアクション空間のサイズです。

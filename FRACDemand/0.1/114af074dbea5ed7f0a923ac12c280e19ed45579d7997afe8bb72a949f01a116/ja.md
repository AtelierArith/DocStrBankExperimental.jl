```
price_elasticities!(problem::FRACProblem;
    monte_carlo_draws::Int=50,
    draw_method::Symbol=:normal,
    antithetic::Bool=false,
    common_draws::Bool=false,
    halton_skip::Int=500)
```

各市場の自己および交差価格弾力性の完全な行列を計算して保存します。追加のキーワード引数はモンテカルロドローを制御します:   • draw*method=:normal または :halton   • antithetic=true は反対称正規分布を使用します（:normal のみ）   • common*draws=true はすべての市場で同じドローを使用します   • halton_skip はハルトン列のスキップ（バーンイン）を設定します

```
dagzigzag(n, G = DiGraph(n); balance = metropolis_balance, prior = (_,_)->1.0, score=UniformScore(),
                    coldness = 1.0, σ = 0.0, ρ = 1.0, 
                    κ = min(n - 1, 10), iterations=10, verbose=false, save=true)
```

因果ジグザグアルゴリズムを、ダグ `G` で開始します。バランス関数 `balance ∈ {metropolis_balance, barker_balance, sqrt}`、スコア関数（`ges` アルゴリズムを参照）およびイテレーションのための冷却パラメータ。`σ = 1.0, ρ = 0.0` は純粋な拡散挙動を与え、`σ = 0.0, ρ = 1.0` はジグザグ挙動を与えます。

情報を含むタプルのベクトルを返します。各タプルには、グラフ、経過時間、現在の方向、エッジの数、およびスコアが含まれます。

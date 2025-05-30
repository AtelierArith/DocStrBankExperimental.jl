```
causalzigzag(n, G = (DiGraph(n), 0); balance = metropolis_balance, prior = (_,_)->1.0, score=UniformScore(),
                    coldness = 1.0, σ = 0.0, ρ = 1.0, naive=false,
                    κ = min(n - 1, 10), iterations=10, verbose=false, save=true)
```

cpdag `(G, t)` で causal zigzag アルゴリズムを実行します。ここで `t` は向き付きまたは向きなしのエッジを持ち、バランス関数 `balance ∈ {metropolis_balance, barker_balance, sqrt}`、スコア関数（`ges` アルゴリズムを参照）およびイテレーションのための冷却パラメータです。`σ = 1.0, ρ = 0.0` は純粋な拡散挙動を与え、`σ = 0.0, ρ = 1.0` はジグザグ挙動を与えます。

情報を含むタプルのベクトルを返します。各タプルにはグラフ、経過時間、現在の方向、エッジの数、およびスコアが含まれます。

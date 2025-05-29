```
LQGProblem(P::ExtendedStateSpace)
```

`ExtendedStateSpace` システムのみが提供される場合、例えば `hinfpartition` からのもので、システム `P` は H₂ 最適制御問題に対応していると仮定されます。

```
C1'C1    = Q1
D12'D12  = Q2
SQ       = C1'D12 # クロステーム

B1*B1'   = R1
D21*D21' = R2
SR       = B1*D21' # クロステーム
```

上記の共分散行列を持つ `LQGProblem` が返されます。返される LQGProblem のシステム記述では `B1 = C1 = I` となります。参考のために、Robust and optimal control の第14章を参照してください。

# 例:

H2 最適コントローラを取得するためのすべての方法は (ほぼ) 同等です。

```julia
using Test
G = ss(tf(1, [10, 1]))
WS = tf(1, [1, 1e-6]) 
WU = makeweight(1e-2, 0.1, 100) 
Gd = hinfpartition(G, WS, WU, [])

K, Gcl = h2synthesize(Gd)              # 最初のオプション、H2 公式を使用
K2, Gcl2 = h2synthesize(Gd, 1000)      # 2番目のオプション、大きな γ を使用した H∞ 公式

lqg = LQGProblem(Gd)                   # 3番目のオプション、LQGProblem に変換してコントローラを取得
K3 = -observer_controller(lqg)

@test h2norm(lft(Gd, K )) ≈ 3.0568 atol=1e-3
@test h2norm(lft(Gd, K2)) ≈ 3.0568 atol=1e-3
@test h2norm(lft(Gd, K3)) ≈ 3.0568 atol=1e-3
```

```
AuxQuadGKJL(; order = 7, norm = norm)
```

Integrals.jlによって提供されるQuadGKJLの一般化で、補助的な積分のための`AuxValue`d被積分関数と、`IntegralProblem`への`batch`引数を使用したマルチスレッド評価を可能にします。

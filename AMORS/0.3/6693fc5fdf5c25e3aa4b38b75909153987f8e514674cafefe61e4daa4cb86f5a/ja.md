```
info.Fxy
AMORS.objective_function(info::AMORS.Info)
AMORS.objective_function(G(x⊗y), μ, J(x), deg(J), ν, K(y), deg(K), α=1)
AMORS.objective_function(G(x⊗y), μ*J(x), deg(J), ν*K(y), deg(K), α=1)
```

はAMORS目的関数の値を生成します：

```
F(α*x, y/α, μ, ν) = F(x, y, μ*|α|^q, ν/|α|^r)
                  = G(x⊗y) + μ*J(x)*|α|^q + ν*K(y)/|α|^r
```

ここで、`q = deg(J)`および`r = deg(K)`は関数`J(x)`および`K(y)`の同次次数です。必要なすべての引数はAMORSアルゴリズムの状態`info`によって提供される場合があります。

```
resilience(N::AbstractUnipartiteNetwork)
```

Gao et al. (2016) によって説明されたレジリエンスパラメータです。これは、単一部分ネットワークのダイナミクスを、次の形の効果的な1D方程式として記述するグローバルパラメータです。

f(xeff) = F(xeff) + βeff G(xeff, xeff)

すなわち、システムの「効果的状態」xeffのダイナミクスに対するネットワークの影響を表す二次項を記述しています。

> Goa, J., Barzael, B. and Barabási 2016. Universal resilience patterns in complex networks. Nature 530(7590), 307-312. doi:10.1038/nature16948


```
sosextractcycle(s::AbstractDiscreteSwitchedSystem, dual, d::Integer;
                ranktols=1e-5, disttols=1e-5)
```

原子占有測度から高成長率のサイクルを抽出します。これは、[`soslyap`](@ref)によって計算された最高成長率の非実現性証明書によって与えられます。この手法の詳細は[LJP17]に記載されています。

  * [LJP17] B. Legat, R. M. Jungers, and P. A. Parrilo.

[Certifying unstability of Switched Systems using Sum of Squares Programming](https://arxiv.org/abs/1710.01814), arXiv preprint arXiv:1710.01814, **2017**.

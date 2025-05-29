```
sosextractcycle(s::AbstractDiscreteSwitchedSystem, dual, d::Integer;
                ranktols=1e-5, disttols=1e-5)
```

Extract cycles of high growth rate from atomic occupation measures given by the infeasibility certificates of highest growth rate computed by [`soslyap`](@ref). The method is detailed in [LJP17].

  * [LJP17] B. Legat, R. M. Jungers, and P. A. Parrilo.

[Certifying unstability of Switched Systems using Sum of Squares Programming](https://arxiv.org/abs/1710.01814), arXiv preprint arXiv:1710.01814, **2017**.

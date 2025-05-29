```julia
FillChis!(chi::Susceptibility; fill_BZ::Bool=false, a::Int64=3, b::Int64=3)
```

関数は、与えられたすべてのΩ=`Omegas`に対して感受性を計算しますが、与えられたパスに存在するすべての`Q`について、`a`と`b`によって与えられた固定の方向に沿って計算します。

```
WaldWolfowitzTest(x::AbstractVector{Bool})
WaldWolfowitzTest(x::AbstractVector{<:Real})
```

与えられたデータがランダムである、または独立してサンプリングされているという帰無仮説の下で、ワルド・ウルフウィッツ（またはランズ）テストを実行します。データは多値または二値（ブール値）として提供できます。多値の場合、サンプルは各要素を中央値より上または下としてラベル付けすることによって変換されます。

実装: [`pvalue`](@ref)

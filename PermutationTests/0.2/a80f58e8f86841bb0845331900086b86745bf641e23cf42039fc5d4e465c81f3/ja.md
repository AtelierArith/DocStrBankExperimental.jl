```julia
function σ²(x::UniData; 
    corrected::Bool=false, 
    centered::Bool=false, 
    mean::Realo=nothing) 
```

xの$N$要素の母分散（デフォルト）または、`corrected`がtrueの場合はその不偏標本推定量。

`centered`がtrueの場合、`x`の要素の二乗の合計を$N$で割った値、または`corrected`がtrueの場合は$N-1$を返します。

そうでない場合は、

引数`corrected`と`mean`を使ってjuliaの標準関数`var`を呼び出します。

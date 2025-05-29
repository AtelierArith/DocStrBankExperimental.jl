```
all_elasticities(problem::FRACProblem, 
    results::Dict{Any,Any}; 
    I = 50, 
    product = 1, 
    by_value = nothing)
```

この関数は、`FRACProblem`と結果の辞書を引数として受け取ります。結果の辞書は、`estimate!`関数の出力である必要があります。これは、ユーザーが直接呼び出すことを意図していない内部関数です。

```
topk(o::PyObject, k::Union{PyObject,Integer}=1;
    sorted::Bool=true, name::Union{Nothing,String}=nothing)
```

最後の次元に対して `k` 個の最大エントリの値とインデックスを見つけます。`sorted=true` の場合、結果の k 要素は値に基づいて降順にソートされます。

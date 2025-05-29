```
JLFor(kernel, iterators::Vector)
```

イテレータのリストから複数のループ式を作成するための便利なコンストラクタです。

# 例

```julia
julia> JLFor([:it1, :it2, :it3]) do i, j, k
    :(kernel_function_call($i, $j, $k))
end
for ##i#291 = it1, ##i#292 = it2, ##i#293 = it3
    kernel_function_call(##i#291, ##i#292, ##i#293)
end
```

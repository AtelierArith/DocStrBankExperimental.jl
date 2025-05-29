```
while_loop(condition::Union{PyObject,Function}, body::Function, loop_vars::Union{PyObject, Array{Any}, Array{PyObject}};
    parallel_iterations::Int64=10, kwargs...)
```

`condition`が真である間、`loop_vars`をループします。この演算子は計算グラフ内のループを示すために1つの追加ノードを作成するだけです。

# 例

以下のスクリプトは次を計算します。

$$
\sum_{i=1}^{10} i
$$

```julia
function condition(i, ta)
    i <= 10
end
function body(i, ta)
    u = read(ta, i-1)
    ta = write(ta, i, u+1)
    i+1, ta
end
ta = TensorArray(10)
ta = write(ta, 1, constant(1.0))
i = constant(2, dtype=Int32)
_, out = while_loop(condition, body, [i, ta])
summation = stack(out)[10]
```

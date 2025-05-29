```
  optimize(
        f::Function, # 目的関数
        search_space,
        method::AbstractAlgorithm = ECA();
        logger::Function = (status) -> nothing,
  )
```

n次元関数 `f` を `search_space` (2×n 行列) の範囲で最小化します。デフォルトでは `method = ECA()` を使用します。

# 例

f(x) = Σx² を最小化します。ここで x ∈ [-10, 10]³。

解:

```jldoctest
julia> f(x) = sum(x.^2)
f (generic function with 1 method)

julia> bounds = [  -10.0 -10 -10; # 下限
                    10.0  10 10 ] # 上限
2×3 Array{Float64,2}:
 -10.0  -10.0  -10.0
  10.0   10.0   10.0

julia> result = optimize(f, bounds)
+=========== RESULT ==========+
  iteration: 1429
    minimum: 2.5354499999999998e-222
  minimizer: [-1.5135301653303966e-111, 3.8688354844737692e-112, 3.082095708730726e-112]
    f calls: 29989
 total time: 0.1543 s
+============================+
```

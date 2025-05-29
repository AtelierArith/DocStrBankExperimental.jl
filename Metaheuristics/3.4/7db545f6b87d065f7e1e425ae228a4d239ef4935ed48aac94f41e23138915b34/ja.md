```
ABC(;
    N = 50,
    Ne = div(N+1, 2),
    No = div(N+1, 2),
    limit=10,
    information = Information(),
    options = Options()
)
```

ABCは人工蜂コロニーアルゴリズムの元のパラメータを実装しています。`N`は個体数、`Ne`は従業員の数、`No`は見張り蜂の数です。`limit`は解が訪問される回数に関連しています。

# 例

```jldoctest
julia> f(x) = sum(x.^2)
f (generic function with 1 method)

julia> optimize(f, [-1 -1 -1; 1 1 1.0], ABC())
+=========== RESULT ==========+
  iteration: 595
    minimum: 4.03152e-28
  minimizer: [1.489845115451046e-14, 1.2207275971717747e-14, -5.671872444705246e-15]
    f calls: 30020
 total time: 0.0360 s
+============================+

julia> optimize(f, [-1 -1 -1; 1 1 1.0], ABC(N = 80,  No = 20, Ne = 50, limit=5))
+=========== RESULT ==========+
  iteration: 407
    minimum: 8.94719e-08
  minimizer: [8.257485723496422e-5, 0.0002852795196258074, -3.5620824723352315e-5]
    f calls: 30039
 total time: 0.0432 s
+============================+
```

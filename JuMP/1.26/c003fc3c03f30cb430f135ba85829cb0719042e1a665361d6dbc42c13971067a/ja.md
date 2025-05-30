```
@constraints(model, args...)
```

一度に制約のグループを追加します。これは[`@constraint`](@ref)マクロと同様の方法です。

モデルは最初の引数でなければならず、複数の制約を`begin ... end`ブロックで複数行にわたって追加できます。

このマクロは、定義された制約を含むタプルを返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, w);

julia> @variable(model, x);

julia> @variable(model, y);

julia> @variable(model, z[1:3]);

julia> @constraints(model, begin
           x >= 1
           y - w <= 2
           sum_to_one[i=1:3], z[i] + y == 1
       end);

julia> print(model)
Feasibility
Subject to
 sum_to_one[1] : y + z[1] = 1
 sum_to_one[2] : y + z[2] = 1
 sum_to_one[3] : y + z[3] = 1
 x ≥ 1
 -w + y ≤ 2
```

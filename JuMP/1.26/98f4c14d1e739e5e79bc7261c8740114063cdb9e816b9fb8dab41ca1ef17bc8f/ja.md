```
@NLconstraints(model, args...)
```

モデルに複数の非線形制約を一度に追加します。これは[`@NLconstraint`](@ref)マクロと同様の方法です。

モデルは最初の引数でなければならず、複数の制約を`begin ... end`ブロック内で複数行にわたって追加できます。

このマクロは、定義された制約を含むタプルを返します。

!!! compat
    このマクロはレガシー非線形インターフェースの一部です。 [非線形モデリング](@ref)に文書化されている新しい非線形インターフェースの使用を検討してください。ほとんどの場合、`@NLconstraints`を[`@constraints`](@ref)に置き換えることができます。


## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @variable(model, y);

julia> @variable(model, t);

julia> @variable(model, z[1:2]);

julia> a = [4, 5];

julia> @NLconstraints(model, begin
           t >= sqrt(x^2 + y^2)
           [i = 1:2], z[i] <= log(a[i])
       end)
((t - sqrt(x ^ 2.0 + y ^ 2.0)) - 0.0 ≥ 0, NonlinearConstraintRef{ScalarShape}[(z[1] - log(4.0)) - 0.0 ≤ 0, (z[2] - log(5.0)) - 0.0 ≤ 0])
```

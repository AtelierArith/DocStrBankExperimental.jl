```
@variables(model, args...)
```

モデルに複数の変数を一度に追加します。これは[`@variable`](@ref)マクロと同様の方法です。

モデルは最初の引数でなければならず、複数の変数は`begin ... end`ブロック内で複数行にわたって追加できます。

このマクロは、定義された変数を含むタプルを返します。

## 例

```jldoctest
julia> model = Model();

julia> @variables(model, begin
           x
           y[i = 1:2] >= 0, (start = i)
           z, Bin, (start = 0, base_name = "Z")
       end)
(x, VariableRef[y[1], y[2]], Z)
```

!!! note
    キーワード引数は括弧内に含める必要があります（上記の例を参照してください）。


```

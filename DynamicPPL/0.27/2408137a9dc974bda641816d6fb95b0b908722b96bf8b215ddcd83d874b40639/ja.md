```
conditioned(model::Model)
```

`model`の条件付き値を返します。

# 例

```jldoctest
julia> using Distributions

julia> using DynamicPPL: conditioned, contextualize

julia> @model function demo()
           m ~ Normal()
           x ~ Normal(m, 1)
       end
demo (generic function with 2 methods)

julia> m = demo();

julia> # 条件を付けたすべての変数とその値を返します。
       conditioned(condition(m, x=100.0, m=1.0))
(x = 100.0, m = 1.0)

julia> # ネストされたものも機能します（`PrefixContext`は結果に何も影響を与えないことに注意してください）。
       cm = condition(contextualize(m, PrefixContext{:a}(condition(m=1.0))), x=100.0);

julia> conditioned(cm)
(x = 100.0, m = 1.0)

julia> # `m`に条件を付けたので、接頭辞が付いた後に表示される`a.m`ではなく、
       # `a.m`はランダム変数として扱われます。
       keys(VarInfo(cm))
1-element Vector{VarName{Symbol("a.m"), typeof(identity)}}:
 a.m

julia> # もし`a.m`に条件を付けると、モデル内の`m`は観測値と見なされます。
       cm = condition(contextualize(m, PrefixContext{:a}(condition(var"a.m"=1.0))), x=100.0);

julia> conditioned(cm).x
100.0

julia> conditioned(cm).var"a.m"
1.0

julia> keys(VarInfo(cm)) # <= サンプリングされた変数はありません
VarName[]
```

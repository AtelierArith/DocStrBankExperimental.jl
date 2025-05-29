```
@vsym(expr)
```

入力変数式 `expr` に対して変数シンボルを返すマクロです。例えば、`@vsym x[1]` は `:x` を返します。

## 例

```jldoctest
julia> @vsym x
:x

julia> @vsym x[1,1][2,3]
:x

julia> @vsym x[end]
:x
```

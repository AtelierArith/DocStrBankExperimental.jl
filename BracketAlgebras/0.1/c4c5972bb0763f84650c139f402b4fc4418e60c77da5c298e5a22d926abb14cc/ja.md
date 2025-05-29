```
standard_violation(t::Tabloid)
```

タブロイド `t` の標準性に対する最初の違反のインデックスを返します。すなわち、`t[i,j]` > `t[i+1, j]` となる最初のインデックスを返します。そうでない場合は `nothing` を返します。

# 例:

```jldoctest
julia> standard_violation(Tabloid([1 2 3; 1 4 5; 1 5 6; 2 3 4], [1,2,3,4,5,6]))
CartesianIndex(3, 2)
```

```jldoctest
julia> standard_violation(Tabloid([1 2 3; 1 2 4], [1,2,3,4]))

```

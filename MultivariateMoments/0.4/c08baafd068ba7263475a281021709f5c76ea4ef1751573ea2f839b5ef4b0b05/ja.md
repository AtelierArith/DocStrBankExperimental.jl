```
struct UserRank <: RankCheck
    pagesize::Int
end
```

ユーザーは、ページサイズ `pagesize` の `REPL.TerminalMenus.RadioMenu` で特異値に基づいてランクを選択します。

## 例

```julia
julia> rank_from_singular_values([1, 1e-1, 5e-2, 1e-5, 5e-6], UserRank())
Choose the last significant singular value:
   1.0
   0.1
 > 0.05
   1.0e-5
   5.0e-6
3
```

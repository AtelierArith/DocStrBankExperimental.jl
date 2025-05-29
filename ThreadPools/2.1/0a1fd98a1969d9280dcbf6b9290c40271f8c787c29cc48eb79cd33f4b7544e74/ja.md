```
poolresults(pool::QueuePool) -> 結果イテレータ
```

プールされたタスクの `fetch` された結果に対するイテレータを返します。

# 例

```julia
julia> pool = QueuePool();

julia> @async begin
         for i in 1:4
           put!(pool, x -> 2*x, i)
         end
         close(pool)
       end;

julia> for r in poolresults(pool)
         println(r)
       end
6
2
4
8
```

スレッド間の実行順序は保証されていないことに注意してください。

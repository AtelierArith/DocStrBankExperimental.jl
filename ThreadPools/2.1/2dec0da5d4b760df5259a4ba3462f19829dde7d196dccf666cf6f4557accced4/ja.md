```
logqmap(fn, itrs...) -> (pool, collection)
```

`Base.map`を模倣しますが、非均一なタスクの所要時間に適したキュー方式のスケジューリング戦略を使用して、すべての利用可能なスレッドに関数評価を開始します。また、ログ記録関数と`plot`で分析できるログ付きプールも返します。

# 例

```julia
julia> (pool, result) = logqmap(1:8) do x
         println((x,Threads.threadid()))
         x^2
        end;
(3, 3)
(4, 4)
(2, 2)
(5, 3)
(7, 2)
(6, 4)
(8, 3)
(1, 1)

julia> result'
1×8 LinearAlgebra.Adjoint{Int64,Array{Int64,1}}:
1  4  9  16  25  36  49  64

julia> plot(pool)
```

実行順序は保証されていませんが、結果の順序は保証されています。また、プライマリスレッドが使用されていることにも注意してください。

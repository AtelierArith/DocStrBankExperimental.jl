```
logtmap(fn, itrs...) -> (pool, collection)
```

`Base.map`を模倣しますが、関数の評価をすべての利用可能なスレッドに対して開始し、均一なタスクの所要時間に適した事前に割り当てられたスケジューリング戦略を使用します。また、ログ記録関数と`plot`で分析できるログ付きプールも返します。

# 例

```julia
julia> (pool, result) = logtmap(1:8) do x
         println((x,Threads.threadid()))
         x^2
       end;
(1, 1)
(3, 2)
(7, 4)
(5, 3)
(8, 4)
(4, 2)
(2, 1)
(6, 3)

julia> result'
1×8 LinearAlgebra.Adjoint{Int64,Array{Int64,1}}:
1  4  9  16  25  36  49  64

julia> plot(pool)
```

実行順序は保証されていませんが、結果の順序は保証されています。また、プライマリスレッドが使用されることに注意してください。

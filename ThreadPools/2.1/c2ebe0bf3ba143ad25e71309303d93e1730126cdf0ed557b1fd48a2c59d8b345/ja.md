```
bforeach(fn, itrs...)
```

`Base.foreach`を模倣しますが、均一なタスクの所要時間に適した事前に割り当てられたスケジューリング戦略を使用して、プライマリ以外のすべての利用可能なスレッドに関数評価を開始します。

# 例

```julia
julia> bforeach(x -> println((x,Threads.threadid())), 1:8)
(1, 2)
(6, 4)
(2, 2)
(7, 4)
(8, 4)
(3, 3)
(4, 3)
(5, 3)
```

実行順序は保証されておらず、プライマリスレッドは使用されないことに注意してください。

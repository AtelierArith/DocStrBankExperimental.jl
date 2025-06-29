```
logqbforeach(fn, itrs...)
```

`Base.foreach`を模倣しますが、プライマリ以外のすべての利用可能なスレッドに関数評価を開始し、非均一なタスクの所要時間に適したキュー方式のスケジューリング戦略を使用します。 ログが記録されたプールを返し、ログ関数や`plot`で分析できます。

# 例

```julia
julia> pool = logqbforeach(x -> println((x,Threads.threadid())), 1:8);
(2, 2)
(1, 3)
(3, 4)
(4, 2)
(5, 3)
(6, 4)
(7, 2)
(8, 3)

julia> plot(pool)
```

実行順序は保証されておらず、プライマリスレッドは使用されないことに注意してください。

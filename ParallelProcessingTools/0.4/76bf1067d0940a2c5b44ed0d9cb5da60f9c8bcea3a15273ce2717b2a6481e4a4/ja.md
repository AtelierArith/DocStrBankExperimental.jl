```
@critical expr
```

`expr`をクリティカルセクションとしてマークします。クリティカルセクション内のコードは、他のクリティカルセクションと並行して（マルチスレッドを介して）実行されることはありません。

`@critical`は、スレッドセーフでないコードをマークするのに非常に便利です。

例:

```julia
@onthreads allthreads() begin
    @critical @info Base.Threads.threadid()
end

`@critical`がなければ、上記は通常Juliaをクラッシュさせます。
```

```
dpmap(fn, args...; mod = Main, kwargs...)
```

「分散プールマップ。」

`Distributed` パッケージの `pmap` のラッパーで、リモートワーカーで分散変数にアクセスできるように、正しいモジュールでコードを実行します。最初の関数 `fn` 以外のすべての引数は `pmap` に渡されます。

関数 `fn` は評価される式を返す必要があります。

# 例

```julia
using Distributed
dpmap(x -> :(computeSomething(someData, $x)), WorkerPool(workers), Vector(1:10))
```

```julia
di = distributeSomeData()
dpmap(x -> :(computeSomething($(di.val), $x)), CachingPool(di.workers), Vector(1:10))
```

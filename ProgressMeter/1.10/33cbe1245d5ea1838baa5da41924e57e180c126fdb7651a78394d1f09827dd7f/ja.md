```
progress_map(f, c...; mapfun=map, progress=Progress(...), kwargs...)
```

進行状況を表示しながら `map`-のような関数を実行します。

`mapfun` は任意の関数を指定できますが、`map`、`reduce`、および `pmap` でのみテストされています。`ProgressMeter.ncalls(::typeof(mapfun), ::Function, args...)` を定義して、`f` への呼び出し回数を指定する必要があります。

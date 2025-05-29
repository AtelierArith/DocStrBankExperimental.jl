```
(advice::Advice)((post::Function, func::Function, args::Tuple, kwargs::NamedTuple))
```

`advice`を関数呼び出し`func(args...; kwargs...)`に適用し、新しい`(post, func, args, kwargs)`タプルを返します。

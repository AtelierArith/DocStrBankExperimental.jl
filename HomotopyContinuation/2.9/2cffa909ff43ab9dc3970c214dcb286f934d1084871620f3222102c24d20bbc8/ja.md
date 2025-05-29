```
trace_test(W::WitnessSet; options...)
```

与えられたウィットネスセット `W` が完全であるかどうかを確認するためにトレーステスト [^LRS18] を実行します。`W` が完全である場合、理論的にはウィットネスセットのトレースは 0 であるべきです。浮動小数点演算のため、これは必ずしもそうではないため、トレースが十分に小さいことを手動で確認する必要があります。パス追跡の失敗によりトレーステストが失敗した場合は `nothing` を返します。`options` は [`witness_set`](@ref) への呼び出しと同じです。

```julia-repl
julia> @var x y;
julia> F = System([x^2 + y^2 - 5], [x, y])
System of length 1
 2 variables: x, y

 -5 + x^2 + y^2

julia> W = witness_set(F)
Witness set for dimension 1 of degree 2

julia> trace = trace_test(W)
9.981960497718987e-16
```

[^LRS18]: Leykin, Anton, Jose Israel Rodriguez, and Frank Sottile. "Trace test." Arnold Mathematical Journal 4.1 (2018): 113-125.

APA

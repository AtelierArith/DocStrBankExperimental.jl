```
MultiplexTraces{names}(trace)
```

同じ長さの2つのトレースを持つ特別な [`AbstractTraces`](@ref) です。そして、これら2つのトレースはヘッダーとテール部分を共有します。

例えば、`trace` が0から9の要素を含む場合、最初の `trace_A` は0から8の要素のビューであり、2番目のものは1から9のビューです。

```
      ┌─────trace_A───┐
trace 0 1 2 3 4 5 6 7 8 9
        └────trace_B────┘
```

これは、RLで `states` と `next_states` を表現するのに非常に一般的です。

```
function lazy_broadcast end # exported
const lazy = lazy_broadcast # not exported
```

この関数にはメソッドがなく、ブロードキャスト式を消費するためだけに使用されることを意図しており、これにより具現化されず、遅延的に使用され、後で消費されることができます。

例えば、複雑なブロードキャスト式を複数のステップに分けて、すべてのコンポーネントを合計したい場合を考えてみましょう：

```julia
julia> function foo(x)
           y = x .+ x
           z = 2 .* y
           sum(z)
       end;

julia> @benchmark foo(v) setup=(v=rand(10))
BenchmarkTools.Trial: 10000 samples with 995 evaluations.
 Range (min … max):  31.405 ns …  4.801 μs  ┊ GC (min … max):  0.00% … 98.56%
 Time  (median):     34.809 ns              ┊ GC (median):     0.00%
 Time  (mean ± σ):   45.504 ns ± 93.354 ns  ┊ GC (mean ± σ):  20.30% ± 11.70%

  █▅▃▂                                                        ▁
  █████▆▅▅▅▅▅▅▁▄▅▅▇▅▃▁▁▁▄▅▅▁▁▁▁▁▃▁▁▁▁▁▄▁▅▁▁▁▁▁▃▅▆▅▄▅▄▁▄▄▆▆▅▄▅ █
  31.4 ns      Histogram: log(frequency) by time       298 ns <

 Memory estimate: 288 bytes, allocs estimate: 4.
 ```

 これは、`y` と `z` のために新しい配列を割り当てる必要があり、ブロードキャストカーネルが「融合」されていないため、データが複数回渡される必要があるため、必要以上に遅くなっています。

`DontMaterialize` は、これらの割り当てを回避し、ブロードキャストの融合を保持するための簡単な方法を提供します：
```

julia julia> function bar(x)            y = lazy*broadcast.(x .+ x)            z = lazy*broadcast.(2 .* y)            sum(z)        end;

julia> @benchmark bar(v) setup=(v=rand(10)) BenchmarkTools.Trial: 10000 samples with 1000 evaluations.  Range (min … max):  5.931 ns … 59.562 ns  ┊ GC (min … max): 0.00% … 0.00%  Time  (median):     6.252 ns              ┊ GC (median):    0.00%  Time  (mean ± σ):   6.435 ns ±  2.767 ns  ┊ GC (mean ± σ):  0.00% ± 0.00%

```
    ▁█
```

▃▂▃▃▄▇██▂▂▂▂▂▂▂▂▂▂▂▂▂▁▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▁▂▂▁▂▂▂▂▂▂▂▂▂▂ ▂   5.93 ns        Histogram: frequency by time        8.75 ns <

Memory estimate: 0 bytes, allocs estimate: 0.

```

`lazy_broadcast` 呼び出しの結果は、`materialize` 関数（ここでは `Base.Broadcast` から再エクスポートされています）を使用して配列に収集できます：

```

julia julia> lazy_broadcast.(2 .* [1,2,3]) Broadcasted{Base.Broadcast.DefaultArrayStyle{1}}(*, (2, [1, 2, 3]))

julia> materialize(ans) 3-element Vector{Int64}:  2  4  6 ```

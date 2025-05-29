# グリュンワルト–レティニコフの意味の分数導関数。

```
fracdiff(f, α, start_point, end_point, GLDirect())
```

### 例:

```julia-repl
julia> fracdiff(x->x^5, 0, 0.5, GLDirect())
```

!!! info "範囲"
    グリュンワルト–レティニコフの意味のfracdiffは$0 < \alpha < 1$のみをサポートしていることに注意してください。


詳細については、[グリュンワルト–レティニコフ導関数](https://en.wikipedia.org/wiki/Gr%C3%BCnwald%E2%80%93Letnikov_derivative)を参照してください。

グリュンワルト・レティニコフの直接計算方法は、分数導関数を取得するためのもので、精度は保証されていますが、より多くのメモリ割り当てとコンパイル時間を引き起こします。

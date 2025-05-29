```julia
solve_unsteady(
;
    setup,
    tlims,
    ustart,
    tempstart,
    method,
    psolver,
    Δt,
    Δt_min,
    cfl,
    n_adapt_Δt,
    docopy,
    processors,
    θ,
    cache
)

```

`method`を使用して非定常問題を解決します。

`Δt`が実数の場合、`(t_end - t_start) / Δt`が整数になるように丸められます。`Δt = nothing`の場合、時間ステップはCFL数`cfl`で`n_adapt_Δt`イテレーションごとに選択されます。`Δt_min`が指定されている場合、適応時間ステップはそれを下回ることはありません。

`processors`は、各時間ステップの後に呼び出されます。

`processor.initialize`関数に渡される`state`可観測量にはデバイス上に存在するベクトルが含まれており、プロセッサ内で`Array(u)`を使用してホストに戻す必要があるかもしれません。

`(; u, t), outputs`を返します。ここで、`outputs`は同じフィールド名を持つ`processors`の出力を含む名前付きタプルです。

```
krylov_solve!(workspace, args...; kwargs...)
```

汎用関数で、`workspace`の型に基づいて適切なインプレース（ブロック）Krylovメソッドにディスパッチします。引数`workspace`は、[`KrylovWorkspace`](@ref)または[`BlockKrylovWorkspace`](@ref)のサブタイプでなければなりません（例えば、`CgWorkspace`、`GmresWorkspace`、または`BlockMinresWorkspace`）。

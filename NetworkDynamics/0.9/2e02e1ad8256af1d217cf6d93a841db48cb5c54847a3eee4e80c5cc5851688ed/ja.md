```
dump_state([IO=stdout], sol, t, idx; sigdigits=5)
```

ネットワークソリューション `sol` を受け取り、指定されたコンポーネントモデルの初期状態とともに `t` の状態を `IO` に出力します（デフォルトは `stdout` です）。

`idx` は有効なコンポーネントインデックス、すなわちシンボル指定なしの `VIndex` または `EIndex` でなければなりません。

```
dump_state(sol, 1.0, VIndex(4))
dump_state(sol, 1.0, EIndex(2))
```

参照: [`dump_initial_state`](@ref).

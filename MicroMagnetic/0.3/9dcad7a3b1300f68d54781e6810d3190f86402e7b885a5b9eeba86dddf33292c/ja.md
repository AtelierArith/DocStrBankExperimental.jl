```
update_zeeman(sim::AbstractSim, H0::TupleOrArrayOrFunction; name="zeeman")
```

H0がその名前に従ったTupleOrArrayOrFunctionである場合、Zeeman場をH0に設定します。例えば、

```julia
   add_zeeman(sim, (0,0,0), name="my_H")  # (0,0,0) A/mの場を持つzeemanエネルギーを作成
   update_zeeman(sim, (0,0,1e5), name="my_H")  # 場を(0,0,1e5) A/mに変更
```

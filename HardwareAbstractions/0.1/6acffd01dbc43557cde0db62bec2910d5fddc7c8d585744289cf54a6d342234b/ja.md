```
output = sysfilter!(s::SysFilter, input)
output = sysfilter!(state, sys::StateSpace, input)
```

フィルタリングされた出力 `y` を返します。`y = Cx+Du, x'=Ax+Bu`

この関数は、信号が動的システムを通じてフィルタリングされる制御ループを実装するために使用されます。すなわち、`U(z) = C(z)E(z)`。`state` を [`init_sysfilter`](@ref) を使用して初期化します。

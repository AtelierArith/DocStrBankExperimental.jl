```
@spec_str(term)
```

仕様プロパティの簡単なインスタンス化を可能にし、入力シンボルに対応する仕様タイプを返します：

```
spec"t" = Temperature()
```

このプロパティは、`spec` 関数とともに、コンパイル時に仕様プロパティを作成することを可能にします：

```julia-repl
julia> Using Unitful,ThermoState,BenchmarkTools

julia> @btime spec(spec"t",232u"°C",false)
  0.001 ns (0 allocations: 0 bytes)
spec(t = 232[°C])
```

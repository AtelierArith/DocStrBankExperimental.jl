```
UGF(msr::Symbol, std::MultiStateSystems.AbstractSTD)
```

特定の測定 `msr` に基づく UGF コンストラクタで、与えられた状態遷移図 `std` に基づいています。

この関数は、状態空間を自動的に縮小し、ユニークな値と関連する確率のみが残るようにします。

# 例

```julia-repl
julia> stdᵍᵉⁿ = solvedSTD(prob  = [0.1,0.2,0.7],
                          power = [0.0u"MW",0.0u"MW",2.0u"MW"])
julia> ugfᵍᵉⁿ = UGF(:power, stdᵍᵉⁿ)
julia> isequal(ugfᵍᵉⁿ.val,[0.0u"MW",2.0u"MW"])
true
```

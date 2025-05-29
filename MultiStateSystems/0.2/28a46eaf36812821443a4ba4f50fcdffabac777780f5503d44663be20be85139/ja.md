```
UGF
```

ugfは、測度`msr`、対応する値`val`、および関連する確率`prb`を含む構造体です。デフォルトのコンストラクタは次のとおりです。

```
UGF(msr::Symbol, val::Vector, prb::Vector; red::Bool=true)
```

これは、与えられた値ベクトル`val`と関連する確率ベクトル`prb`に基づく特定の測度`msr`のUGFコンストラクタです。

この関数は、状態空間を自動的に縮小し、ユニークな値と関連する確率のみが残るようにします。この動作は、オプションの引数`rdc=false`を渡すことで回避できます。

# 例

```julia-repl
julia> ugfᵍᵉⁿ = UGF(:power, [0.0u"MW",0.0u"MW",2.0u"MW"], [0.1,0.2,0.7])
julia> isequal(ugfᵍᵉⁿ.val, [0.0u"MW",2.0u"MW"])
true
julia> ugfᵍᵉⁿ = UGF(:power, [0.0u"MW",0.0u"MW",2.0u"MW"], [0.1,0.2,0.7], rdc=false)
julia> isequal(ugfᵍᵉⁿ.val, [0.0u"MW",0.0u"MW",2.0u"MW"])
true
```

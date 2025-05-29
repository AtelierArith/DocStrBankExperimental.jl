```
GapObj
```

これは、"即時"（ブール値、小さな整数、FFE）ではないすべてのGAPオブジェクトのJulia型です。

# 例

```jldoctest
julia> typeof(GapObj([1, 2]))          # GAPリスト
GapObj

julia> typeof(GapObj(Dict(:a => 1)))   # GAPレコード
GapObj

julia> typeof( GAP.evalstr( "(1,2,3)" ) )  # GAP置換
GapObj

julia> typeof( GAP.evalstr( "2^64" ) )     # 大きなGAP整数
GapObj

julia> typeof( GAP.evalstr( "2^59" ) )     # 小さなGAP整数
Int64

julia> typeof( GAP.evalstr( "Z(2)" ) )     # GAP FFE
FFE

julia> typeof( GAP.evalstr( "true" ) )     # ブール値
Bool
```

これは、GAPオブジェクトに対するJuliaの見方であることに注意してください。GAPの観点から見ると、Juliaオブジェクトへのポインタも"非即時GAPオブジェクト"として実装されていますが、Juliaにとっては"二重ラップ"ではなく、Juliaオブジェクトとして表示されます。

# 例

```jldoctest
julia> GAP.evalstr( "Julia.Base" )
Base

julia> typeof( GAP.evalstr( "Julia.Base" ) )        # ネイティブJuliaオブジェクト
Module
```

`GapObj`をコンストラクタとして使用して、JuliaオブジェクトをGAPオブジェクトに変換することができます。詳細は[`GapObj(x, cache::GapCacheDict = nothing; recursive::Bool = false)`](@ref)を参照してください。

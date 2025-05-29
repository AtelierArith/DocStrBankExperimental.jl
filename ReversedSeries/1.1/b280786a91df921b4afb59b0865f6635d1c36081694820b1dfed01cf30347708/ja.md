```julia
struct ReversedFrame{df<:DataFrames.DataFrame}
```

  * `__df::DataFrames.DataFrame`
  * `__s::Dict`

これは、DataFrame全体の逆転したビューを提供します。

# 例

```julia-repl
julia> rf = ReversedFrame(btcusd) # btcusdはDataFrameです
julia> rf.ts[1] # 最も最近のタイムスタンプ
julia> rf.ts[2] # その前のタイムスタンプ
julia> rf.c[1]  # 1のクローズは1のタイムスタンプに対応します
julia> rf.o[1] == btcusd.o[end]
true
```

  * インデックス1は起点で、現在の時間を表します。
  * 高いインデックスは過去に遡ります。
  * これは、TradingViewのPineScriptでのシリーズのインデックス付けに似ていますが、彼らは0ベースのインデックスを使用します。

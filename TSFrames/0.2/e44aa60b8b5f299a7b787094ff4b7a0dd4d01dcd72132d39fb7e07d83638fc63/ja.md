# ローリング関数

```julia
rollapply(ts::TSFrame, fun::Function, windowsize::Int; bycolumn=true)
```

関数 `fun` を `ts` のローリングウィンドウに適用します。出力は、各ウィンドウの最後のインデックス値でインデックス付けされた `(nrow(ts) - windowsize + 1)` 行を持つ `TSFrame` オブジェクトです。

`bycolumn` 引数は、`fun` を各列に対して個別に適用する場合は `true`（デフォルト）に設定し、`fun` が全体の `TSFrame` を入力として受け取る場合は `false` に設定する必要があります。

# 例

```jldoctest; setup = :(using TSFrames, DataFrames, Statistics, StatsModels, StatsBase, GLM, Dates)
julia> rollapply(TSFrame([1:10 11:20]), mean, 5)
6×2 TSFrame with Int64 Index
 Index  rolling_x1_mean  rolling_x2_mean 
 Int64  Float64          Float64         
─────────────────────────────────────────
     5              3.0             13.0
     6              4.0             14.0
     7              5.0             15.0
     8              6.0             16.0
     9              7.0             17.0
    10              8.0             18.0

julia> dates = Date(2001, 1, 1):Day(1):Date(2001, 1, 10);
julia> df = DataFrame(Index=dates, inrchf=1:10, usdchf=1:10, eurchf=1:10, gbpchf=1:10, jpychf=1:10);
julia> ts = TSFrame(df)
10×5 TSFrame with Date Index
 Index       inrchf  usdchf  eurchf  gbpchf  jpychf 
 Date        Int64   Int64   Int64   Int64   Int64  
────────────────────────────────────────────────────
 2001-01-01       1       1       1       1       1
 2001-01-02       2       2       2       2       2
 2001-01-03       3       3       3       3       3
 2001-01-04       4       4       4       4       4
 2001-01-05       5       5       5       5       5
 2001-01-06       6       6       6       6       6
 2001-01-07       7       7       7       7       7
 2001-01-08       8       8       8       8       8
 2001-01-09       9       9       9       9       9
 2001-01-10      10      10      10      10      10

julia> function regress(ts)     # 複数回帰のための関数を定義
            ll = lm(@formula(inrchf ~ usdchf + eurchf + gbpchf + jpychf), ts.coredata[:, Not(:Index)])
            co = coef(ll)[coefnames(ll) .== "usdchf"]
            sd = Statistics.std(residuals(ll))
            return (co, sd)
       end

julia> rollapply(ts, regress, 5; bycolumn=false)    # 複数回帰を実行
6×1 TSFrame with Date Index
 Index       rolling_regress      
 Date        Tuple…               
──────────────────────────────────
 2001-01-05  ([1.0], 9.93014e-17)
 2001-01-06  ([1.0], 1.27168e-15)
 2001-01-07  ([1.0], 4.86475e-16)
 2001-01-08  ([1.0], 7.43103e-16)
 2001-01-09  ([1.0], 7.45753e-15)
 2001-01-10  ([1.0], 9.28561e-15)
```

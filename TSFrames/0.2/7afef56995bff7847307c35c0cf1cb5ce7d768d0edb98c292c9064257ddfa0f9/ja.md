# 結合/列結合

```julia
join(ts1::TSFrame, ts2::TSFrame, ts...; jointype::Symbol=:JoinAll)
```

`TSFrame` オブジェクトは、列キーとして `Index` を使用して列方向に結合できます。現在、可能な列結合操作は4種類あります。各結合操作は `Index` 列に対して集合演算を実行し、その後集合演算の出力に基づいてデータセットをマージすることによって機能します。各操作は、TSFrame オブジェクト間で重複する列名に遭遇した場合、最終オブジェクトの列名を自動的に変更します。

サポートされている結合タイプは次のとおりです：

`join(ts1::TSFrame, ts2::TSFrame; jointype=:JoinInner)` および `join(ts1::TSFrame, ts2::TSFrame; jointype=:JoinBoth)`

いわゆる内部結合で、`ts1` と `ts2` のインデックスの交差を取り、その後両方のオブジェクトの列をマージします。結果のオブジェクトには、両方のオブジェクトのインデックスに存在する行のみが含まれます。関数は、TSFrame オブジェクトで同じ名前の列があった場合、最終オブジェクトの列名を変更します。

`join(ts1::TSFrame, ts2::TSFrame; jointype=:JoinOuter)` および `join(ts1::TSFrame, ts2::TSFrame; jointype=:JoinAll)`：

いわゆる外部結合で、`ts1` と `ts2` のインデックスの和集合を取り、その後入力オブジェクトの他の列をマージします。出力には、すべての入力オブジェクトに存在する行が含まれ、オブジェクトのいずれかに行が存在しない場合は `missing` 値が挿入されます。これは、`jointype` が提供されていない場合のデフォルトの動作です。

`join(ts1::TSFrame, ts2::TSFrame; jointype=:JoinLeft)`：

左結合は、左オブジェクト `ts1` に存在するインデックス値を取り、右オブジェクト `ts2` で一致するインデックス値を見つけます。結果のオブジェクトには、左オブジェクトのすべての行、左オブジェクトの列値、および右側の一致するインデックス行に関連付けられた値が含まれます。この操作は、右オブジェクトの一致しない行に `missing` 値を挿入します。

`join(ts1::TSFrame, ts2::TSFrame; jointype=:JoinRight)`

右結合は、左結合と似ていますが、逆方向に機能します。最終オブジェクトには、右オブジェクトのすべての行が含まれ、左オブジェクトから欠落している行には `missing` 値が挿入されます。

デフォルトの動作は、`join` メソッドに `jointype` が提供されていない場合、`jointype=:JoinAll` と仮定することです。

複数の `TSFrame` の結合もサポートされています。構文は次のとおりです。

`join(ts1::TSFrame, ts2::TSFrame, ts...; jointype::Symbol)`

ここで、`jointype` は `:JoinInner`、`:JoinBoth`、`:JoinOuter`、`:JoinAll`、`:JoinLeft` または `:JoinRight` のいずれかでなければなりません。複数の `TSFrame` に対する `join` は左結合的であることに注意してください。

`cbind` は `join` メソッドのエイリアスです。

# 例

```jldoctest; setup = :(using TSFrames, DataFrames, Dates, Random, Statistics)
julia> using Random;

julia> random(x) = rand(MersenneTwister(123), x);

julia> dates = collect(Date(2017,1,1):Day(1):Date(2017,1,10));

julia> ts1 = TSFrame(random(length(dates)), dates);
julia> show(ts1)
(10 x 1) TSFrame with Dates.Date Index

 Index       x1
 Date        Float64
───────────────────────
 2017-01-01  0.768448
 2017-01-02  0.940515
 2017-01-03  0.673959
 2017-01-04  0.395453
 2017-01-05  0.313244
 2017-01-06  0.662555
 2017-01-07  0.586022
 2017-01-08  0.0521332
 2017-01-09  0.26864
 2017-01-10  0.108871

julia> dates = collect(Date(2017,1,1):Day(1):Date(2017,1,30));

julia> ts2 = TSFrame(random(length(dates)), dates);
julia> show(ts2)
30×1 TSFrame with Date Index
 Index       x1
 Date        Float64
───────────────────────
 2017-01-01  0.768448
 2017-01-02  0.940515
 2017-01-03  0.673959
 2017-01-04  0.395453
 2017-01-05  0.313244
 2017-01-06  0.662555
 2017-01-07  0.586022
 2017-01-08  0.0521332
 2017-01-09  0.26864
 2017-01-10  0.108871
 2017-01-11  0.163666
 2017-01-12  0.473017
 2017-01-13  0.865412
 2017-01-14  0.617492
 2017-01-15  0.285698
 2017-01-16  0.463847
 2017-01-17  0.275819
 2017-01-18  0.446568
 2017-01-19  0.582318
 2017-01-20  0.255981
 2017-01-21  0.70586
 2017-01-22  0.291978
 2017-01-23  0.281066
 2017-01-24  0.792931
 2017-01-25  0.20923
 2017-01-26  0.918165
 2017-01-27  0.614255
 2017-01-28  0.802665
 2017-01-29  0.555668
 2017-01-30  0.940782

# すべてのインデックス値で結合
# `join(ts1, ts2; jointype=:JoinAll)` 呼び出しに相当
julia> join(ts1, ts2)
(30 x 2) TSFrame with Date Index
 Index       x1               x1_1
 Date        Float64?         Float64?
────────────────────────────────────────
 2017-01-01        0.768448   0.768448
 2017-01-02        0.940515   0.940515
 2017-01-03        0.673959   0.673959
 2017-01-04        0.395453   0.395453
 2017-01-05        0.313244   0.313244
 2017-01-06        0.662555   0.662555
 2017-01-07        0.586022   0.586022
 2017-01-08        0.0521332  0.0521332
 2017-01-09        0.26864    0.26864
 2017-01-10        0.108871   0.108871
     ⋮              ⋮             ⋮
 2017-01-22  missing          0.291978
 2017-01-23  missing          0.281066
 2017-01-24  missing          0.792931
 2017-01-25  missing          0.20923
 2017-01-26  missing          0.918165
 2017-01-27  missing          0.614255
 2017-01-28  missing          0.802665
 2017-01-29  missing          0.555668
 2017-01-30  missing          0.940782
                         11 行省略

# `join()` のエイリアス
julia> cbind(ts1, ts2);

# 一般的なインデックス値のみを結合
julia> join(ts1, ts2; jointype=:JoinBoth)
(10 x 2) TSFrame with Date Index
 Index       x1         x1_1
 Date        Float64    Float64
──────────────────────────────────
 2017-01-01  0.768448   0.768448
 2017-01-02  0.940515   0.940515
 2017-01-03  0.673959   0.673959
 2017-01-04  0.395453   0.395453
 2017-01-05  0.313244   0.313244
 2017-01-06  0.662555   0.662555
 2017-01-07  0.586022   0.586022
 2017-01-08  0.0521332  0.0521332
 2017-01-09  0.26864    0.26864
 2017-01-10  0.108871   0.108871

# `ts1` のインデックス値を保持
julia> join(ts1, ts2; jointype=:JoinLeft)
(10 x 2) TSFrame with Date Index
 Index       x1         x1_1
 Date        Float64    Float64?
──────────────────────────────────
 2017-01-01  0.768448   0.768448
 2017-01-02  0.940515   0.940515
 2017-01-03  0.673959   0.673959
 2017-01-04  0.395453   0.395453
 2017-01-05  0.313244   0.313244
 2017-01-06  0.662555   0.662555
 2017-01-07  0.586022   0.586022
 2017-01-08  0.0521332  0.0521332
 2017-01-09  0.26864    0.26864
 2017-01-10  0.108871   0.108871

# `ts2` のインデックス値を保持
julia> join(ts1, ts2; jointype=:JoinRight)
(30 x 2) TSFrame with Date Index
 Index       x1               x1_1
 Date        Float64?         Float64
────────────────────────────────────────
 2017-01-01        0.768448   0.768448
 2017-01-02        0.940515   0.940515
 2017-01-03        0.673959   0.673959
 2017-01-04        0.395453   0.395453
 2017-01-05  0.313244   0.313244
 2017-01-06  0.662555   0.662555
 2017-01-07  0.586022   0.586022
 2017-01-08  0.0521332  0.0521332
 2017-01-09  0.26864    0.26864
 2017-01-10  0.108871   0.108871
     ⋮              ⋮             ⋮
 2017-01-22  missing          0.291978
 2017-01-23  missing          0.281066
 2017-01-24  missing          0.792931
 2017-01-25  missing          0.20923
 2017-01-26  missing          0.918165
 2017-01-27  missing          0.614255
 2017-01-28  missing          0.802665
 2017-01-29  missing          0.555668
 2017-01-30  missing          0.940782
                         11 行省略

julia> dates = collect(Date(2017,1,1):Day(1):Date(2017,1,30));

julia> ts3 = TSFrame(random(length(dates)), dates);
julia> show(ts3)
30×1 TSFrame with Date Index
 Index       x1
 Date        Float64
───────────────────────
 2017-01-01  0.768448
 2017-01-02  0.940515
 2017-01-03  0.673959
 2017-01-04  0.395453
 2017-01-05  0.313244
 2017-01-06  0.662555
 2017-01-07  0.586022
 2017-01-08  0.0521332
 2017-01-09  0.26864
 2017-01-10  0.108871
 2017-01-11  0.163666
 2017-01-12  0.473017
 2017-01-13  0.865412
 2017-01-14  0.617492
 2017-01-15  0.285698
 2017-01-16  0.463847
 2017-01-17  0.275819
 2017-01-18  0.446568
 2017-01-19  0.582318
 2017-01-20  0.255981
 2017-01-21  0.70586
 2017-01-22  0.291978
 2017-01-23  0.281066
 2017-01-24  0.792931
 2017-01-25  0.20923
 2017-01-26  0.918165
 2017-01-27  0.614255
 2017-01-28  0.802665
 2017-01-29  0.555668
 2017-01-30  0.940782

# 複数の TSFrame オブジェクトを結合
julia> join(ts1, ts2, ts3; jointype=:JoinLeft)
10×3 TSFrame with Date Index
 Index       x1         x1_1       x1_2
 Date        Float64    Float64?   Float64?
─────────────────────────────────────────────
 2017-01-01  0.768448   0.768448   0.768448
 2017-01-02  0.940515   0.940515   0.940515
 2017-01-03  0.673959   0.673959   0.673959
 2017-01-04  0.395453   0.395453   0.395453
 2017-01-05  0.313244   0.313244   0.313244
 2017-01-06  0.662555   0.662555   0.662555
 2017-01-07  0.586022   0.586022   0.586022
 2017-01-08  0.0521332  0.0521332  0.0521332
 2017-01-09  0.26864    0.26864    0.26864
 2017-01-10  0.108871   0.108871   0.108871

```

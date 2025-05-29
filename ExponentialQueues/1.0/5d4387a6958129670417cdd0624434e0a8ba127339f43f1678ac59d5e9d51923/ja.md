`ExponentialQueue()` は、最大 `N` のイベントを保持する更新可能なキューで、ID は `1...N` で、定常レートは Q[1] ... Q[N] です。これは連続時間でのサンプリングを目的としています。

julia> Q = ExponentialQueue() ExponentialQueue(Accumulator{Float64, +, zero}([Float64[]]), [0, 0, 0, 0, 0, 0, 0, 0, 0, 0  …  0, 0, 0, 0, 0, 0, 0, 0, 0, 0], Int64[])

julia> Q[1] = 1.2 #イベント 1 のレートを更新 1.2

julia> Q[55] = 2.3 #イベント 55 のレートを更新 2.3

julia> i,t = pop!(Q) # 次のイベントの時間とIDを取得し、キューから削除します (55, 0.37869716808319576)

関連情報: `ExponentialQueueDict`

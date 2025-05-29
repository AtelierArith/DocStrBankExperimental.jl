allocframetrcs(io)

JavaSeisデータセットの1フレーム分のトレースのためのメモリを割り当てます。 `Array{Float32,2}`を返します。例えば、`trcs = allocframetrcs(jsopen("data.js"))`。

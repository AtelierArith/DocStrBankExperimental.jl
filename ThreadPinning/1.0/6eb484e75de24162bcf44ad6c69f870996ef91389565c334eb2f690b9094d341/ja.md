`Dict{Int, Vector{Int}}`を返します。ここで、キーはJuliaワーカーのpidで、値は現在ワーカーのJuliaスレッドを実行しているCPUスレッドのCPU IDです。

`include_master=true`の場合、マスタープロセス（`Distributed.myid() == 1`）が含まれます。

`Dict{Int, Vector{Bool}}`を返します。ここで、キーはJuliaワーカーのpidで、値はワーカーのすべてのJuliaスレッドに対して評価された`ThreadPinning.ispinned`の結果です。

`include_master=true`の場合、マスタープロセス（`Distributed.myid() == 1`）が含まれます。

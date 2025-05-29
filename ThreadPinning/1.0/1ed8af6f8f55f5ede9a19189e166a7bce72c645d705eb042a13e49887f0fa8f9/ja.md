`Dict{Int, String}`を返します。ここで、キーはJuliaワーカーのpidで、値はそれぞれのワーカーを現在ホストしているノードのホスト名です。

`include_master=true`の場合、マスタープロセス（`Distributed.myid() == 1`）が含まれます。

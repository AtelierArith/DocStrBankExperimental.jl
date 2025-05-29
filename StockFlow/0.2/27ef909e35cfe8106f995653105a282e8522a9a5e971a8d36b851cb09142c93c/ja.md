ノード名のベクターと、エッジとして機能する頂点のインデックスを示す2つのベクターからCausalLoopPolを作成します。

to_clp([:A, :B], [1 => 2], Vector{Pair{Int, Int}}())は、AからBへの正の極性エッジを持つCausalLoopPolを作成します。

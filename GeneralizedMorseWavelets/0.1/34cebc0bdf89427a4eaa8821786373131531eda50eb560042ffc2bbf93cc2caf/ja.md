gmw_grid(β, γ, J, Q; wmin=0,wmax=pi,phase=0.)

一般化モースウェーブレットのグリッドを作成します。グリッドは、最初のウェーブレットを最低スケールで周波数ピーク `wmax` で初期化することから始まり、その後、`2^(1/JQ)` の係数でスケーリングすることによって次のウェーブレットを生成します。`J` はオクターブの数、`Q` はオクターブ間の数です。結果として `JQ` のウェーブレットのグリッドが得られます。

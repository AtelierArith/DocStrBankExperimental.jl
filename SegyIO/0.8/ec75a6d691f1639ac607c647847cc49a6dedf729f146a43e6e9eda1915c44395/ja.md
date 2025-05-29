使用法:   read*con(con::SeisCon;                  blocks::Array{Int,1} = Array(1:length(con)),                 prealloc*traces::Int = 50000)

'con' から 'blocks' を読み取り、サイズ (ns x prealloc_traces) の事前割り当て配列に格納します。

事前に割り当てられたメモリが満杯になると、'prealloc_traces' によって再度拡張されます。

[`p4est_lnodes_buffer_t`](@ref) は、ノードに関連するデータの通信を処理します。

*send_buffers* は配列の配列であり、現在のプロセスがノードデータを送信する各プロセスに対して1つのバッファがあります。これは、shared***begin と shared***end の呼び出しの間に変更されるべきではありません。

*recv_buffers* は lnodes*share*all** で使用される配列の配列です。*recv*buffers*[j] は lnodes->sharers[j] に対応しており、*lnodes*->sharers[j]->shared*nodes と同じ長さです。lnodes*share*all または lnodes*share*all*end の完了時に、recv*buffers[j] にはプロセス lnodes->sharers[j]->rank からのノードデータが含まれます（j が現在のランクである場合を除き、その場合 recv*buffers[j] は空です）。

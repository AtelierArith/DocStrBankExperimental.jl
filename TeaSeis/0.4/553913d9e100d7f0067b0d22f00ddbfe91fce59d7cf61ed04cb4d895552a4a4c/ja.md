allocframehdrs(io)

JavaSeisデータセットの1フレームのヘッダー用のメモリを割り当てます。 `Array{UInt8,2}`を返します。例えば、`hdrs = allocframehdrs(jsopen("data.js"))`。

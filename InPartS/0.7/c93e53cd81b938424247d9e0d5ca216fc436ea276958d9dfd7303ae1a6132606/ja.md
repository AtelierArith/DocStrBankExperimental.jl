readsim(f; snap = InPartS.lastfullsnap(f), [warn = IOWARN[]], [kwargs...]) readsim(filename; snap, [warn = IOWARN[]], [kwargs...]) ファイルからシミュレーションを読み込み、指定されたスナップショットをロードします。デフォルトでは、最後の完全なスナップショット（[`lastfullsnap`](@ref)を参照）になります。

追加のキーワード引数は、[`readstatic`](@ref)および[`readsnap`](@ref)に渡されます。

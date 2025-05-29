`rio(io::IO=stdout;p...)` は `p` の属性で `io` を強化します。常に `limit=true` で強化され、REPL での表示を模倣します。

したがって、`print(rio(),x...)` は REPL で `x...` を印刷するのと同じです。

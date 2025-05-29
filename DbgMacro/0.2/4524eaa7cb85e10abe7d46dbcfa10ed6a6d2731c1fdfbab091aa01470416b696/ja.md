```
@dbg <expr1> <expr2> <expr3> ...
```

すべての式を `@show` と同じ方法で表示し、それぞれを別の行にし、`module:file:line` 形式の位置情報を前に付けます。

出力は `stderr` に送られます。

デバッグに役立ちます。

# 例

```jldoctest
julia> m = [1 2; 3 4];

julia> @dbg 1+2 "Hello" m
Main:none:1  1 + 2 = 3
Main:none:1  "Hello" = "Hello"
Main:none:1  m = [1 2; 3 4]
```

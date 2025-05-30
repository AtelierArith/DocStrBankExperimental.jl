```
uprint([io::IO], A, [method])
```

`A` のバイナリ Unicode 表現を `io` に書き込みます（`io` が指定されていない場合はデフォルトの出力ストリーム `stdout` に書き込みます）。`true` またはゼロより大きい値を埋め込みます。

印刷方法は、`:braille`、`:block`、`:quadrant`、`:sextant`、または `:octant` のいずれかを渡すことで指定できます。デフォルトは `:braille` です。(`:octant` は、Unicode 16 をサポートするフォントまたはターミナルエミュレーターが必要です。そうでない場合、出力は奇妙に見えるでしょう。)

# 例

```julia-repl
julia> A = rand(Bool, 8, 8)
8×8 Matrix{Bool}:
 0  1  0  1  0  1  0  1
 0  1  1  1  0  1  1  1
 1  0  0  0  0  0  0  0
 0  0  0  0  1  1  1  1
 1  1  0  0  0  1  1  1
 1  1  1  0  1  1  0  0
 0  0  1  0  0  1  0  1
 1  1  0  1  1  1  0  0

julia> uprint(A)
⠜⠚⣘⣚
⣛⢆⣺⠩
julia> uprint(A, :block)
 █▄█ █▄█
▀   ▄▄▄▄
██▄ ▄█▀▀
▄▄▀▄▄█ ▀
```

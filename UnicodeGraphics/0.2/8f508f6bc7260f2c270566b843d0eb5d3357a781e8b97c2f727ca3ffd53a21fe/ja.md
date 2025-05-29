```
ustring(A, [method])
```

`A` のバイナリ Unicode 表現を含む文字列を返し、`true` またはゼロより大きい値を埋めます。

印刷方法は、`:braille`、`:block`、`:quadrant`、`:sextant`、または `:octant` のいずれかを渡すことで指定できます。デフォルトは `:braille` です。(`:octant` は、Unicode 16 をサポートするフォントまたはターミナルエミュレーターが必要です。そうでない場合、出力は奇妙に見えるでしょう。)

# 例

```julia-repl
julia> A = rand(Bool, 8, 8)
8×8 Matrix{Bool}:
 1  1  1  1  0  1  0  0
 1  0  0  1  1  1  0  0
 1  0  0  0  1  0  1  0
 1  0  1  0  1  1  1  1
 0  0  0  0  0  0  1  0
 0  1  1  0  1  0  0  1
 0  0  1  0  0  1  1  1
 1  1  1  1  0  0  1  1

julia> ustring(A)
"⡏⡙⣞⣄
⣐⣆⠢⣵
"

julia> ustring(A, :block)
"█▀▀█▄█  
█ ▄ █▄█▄
 ▄▄ ▄ ▀▄
▄▄█▄ ▀██
"
```

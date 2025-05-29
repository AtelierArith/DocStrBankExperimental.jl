```
ustring(f, A, [method])
```

`A`のバイナリUnicode表現を含む文字列を返し、`f`が`true`を返す値を埋めます。

印刷方法は、`:braille`、`:block`、`:quadrant`、`:sextant`、または`:octant`のいずれかを渡すことで指定できます。デフォルトは`:braille`です。(`:octant`は、Unicode 16をサポートするフォントまたはターミナルエミュレーターが必要です。そうでない場合、出力は奇妙に見えます。)

# 例

```julia-repl
julia> A = rand(1:9, 8, 8)
8×8 Matrix{Int64}:
 8  7  9  6  9  8  3  7
 9  9  3  3  5  5  3  2
 1  6  8  3  7  9  3  7
 9  4  4  7  8  7  3  4
 3  8  7  2  2  1  6  6
 4  8  9  4  1  3  4  6
 4  9  6  2  3  4  8  4
 7  2  7  9  8  2  6  7

julia> ustring(iseven, A)
"⢡⡌⡈⢐
⢞⠼⣡⡿
"

julia> ustring(>(3), A, :block)
"██▀▀██ ▀
▄██▄██ █
▄██▄  ██
█▀█▄▄▀██
"
```

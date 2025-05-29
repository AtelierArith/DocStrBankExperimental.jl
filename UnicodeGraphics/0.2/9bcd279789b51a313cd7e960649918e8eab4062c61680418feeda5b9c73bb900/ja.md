```
uprint([io::IO], f, A, [method])
```

`io` に書き込みます（`io` が指定されていない場合はデフォルトの出力ストリーム `stdout` に書き込みます）`A` のバイナリ Unicode 表現を、`f` が `true` を返す値で埋めます。

印刷方法は、`:braille`、`:block`、`:quadrant`、`:sextant`、または `:octant` のいずれかを渡すことで指定できます。デフォルトは `:braille` です。（`:octant` は、Unicode 16 をサポートするフォントまたはターミナルエミュレーターが必要です。そうでない場合、出力は奇妙に見えるでしょう。）

# 例

```julia-repl
julia> A = rand(1:9, 8, 8)
8×8 Matrix{Int64}:
 9  1  6  3  4  2  9  6
 4  1  2  8  2  5  9  1
 7  5  6  1  1  4  8  8
 4  8  3  4  8  7  8  8
 4  2  2  6  2  6  1  7
 9  1  4  1  8  1  6  1
 3  8  4  3  9  5  5  6
 1  4  4  2  8  6  3  9

julia> uprint(iseven, A)
⣂⢗⡫⣬
⢩⣏⣋⠢
julia> uprint(>(3), A, :block)
█ ▀▄▀▄█▀
██▀▄▄███
█ ▄▀▄▀▄▀
 ██ ██▀█
```

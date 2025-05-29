使用法は[proconio-rs](https://github.com/statiolake/proconio-rs)に似ています。変数名とその構造を指定する必要があります。

```julia
@input a = Int
```

複数の変数はブロック内にネストする必要があります。

```julia
@input begin
    a = Char
    b = Float32
    c = (Int, Char)
    d = String
    e = Bool
end
```

配列は`[type; shape]`の形式で指定する必要があります。

```julia
@input begin
    a = [Int; 3]
    b = [Float32; (2, 3)]
end
```

複雑な構造も扱うことができます。

```julia
@input a = [(Int, [Int; (2, 2)], Char); (2, 2)]
```

CPでは、配列のサイズは通常入力自体によって指定されます。これは、すでに読み込まれた変数を使用することで処理できます。

[ProconIO.jl](https://github.com/lucifer1004/ProconIO.jl)は、CPで一般的に使用される行優先ではなく、Juliaの列優先の規約に従っていることに注意してください。したがって、配列を読み込む際には行と列のインデックスを入れ替える必要があるかもしれません。

```julia
@input begin
    n = Int
    m = Int
    v = [Int; (m, n)]
end
```

行優先のスタイルを好む場合は、ベクトルのベクトルを代わりに使用できます。

```julia
@input begin
    n = Int
    m = Int
    v = [[Int; m]; n]
end
```

時には、入力が可変長のベクトルのベクトルであることがあります。これは、形状を省略し、代わりに入力から読み込むことで処理できます。以下のコードは、`n`個の可変長ベクトルのベクトルを読み込みます。

```julia
@input begin
    n = Int
    v = [[Int; ]; n]
end
```

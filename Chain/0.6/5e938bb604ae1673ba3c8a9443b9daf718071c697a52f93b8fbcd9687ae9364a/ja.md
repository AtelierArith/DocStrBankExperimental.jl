```
@chain(expr, exprs...)
```

一連の式をチェーンに書き換えます。ここで、1つの式の結果が次の式に特定のルールに従って挿入されます。

**ルール 1**

`begin ... end` ブロックである任意の `expr` はフラット化されます。例えば、これらの2つの擬似コードは同等です：

```julia
@chain a b c d e f

@chain a begin
    b
    c
    d
end e f
```

**ルール 2**

フラット化された表現の最初の式以外のすべての式は、前の結果が最初の引数として挿入されます。ただし、少なくとも1つのアンダースコア `_` が存在する場合は、その場合、すべてのアンダースコアは前の結果で置き換えられます。

式がシンボルである場合、そのシンボルは関数呼び出しと同等に扱われます。

例えば、次のコードブロックは

```julia
@chain begin
    x
    f()
    @g()
    h
    @i
    j(123, _)
    k(_, 123, _)
end
```

は次のように等価です：

```julia
begin
    local temp1 = f(x)
    local temp2 = @g(temp1)
    local temp3 = h(temp2)
    local temp4 = @i(temp3)
    local temp5 = j(123, temp4)
    local temp6 = k(temp5, 123, temp5)
end
```

**ルール 3**

`@aside` で始まる式は、その結果を次の式に渡しません。代わりに、前の式の結果が渡されます。これはチェーンの状態を検査するためのものです。`@aside` 内の式には前の結果が自動的に挿入されず、アンダースコアを使用してそれを参照できます。

```julia
@chain begin
    [1, 2, 3]
    filter(isodd, _)
    @aside @info "フィルタリング後の要素数は $(length(_)) です"
    sum
end
```

**ルール 4**

変数の代入で式を開始することが許可されています。この場合、その代入の右辺に通常の挿入ルールが適用されます。これは中間結果を保存するために使用できます。

```julia
@chain begin
    [1, 2, 3]
    filtered = filter(isodd, _)
    sum
end

filtered == [1, 3]
```

**ルール 5**

`@.` マクロはシンボルと共に使用して、その関数を前の結果に対してブロードキャストすることができます。

```julia
@chain begin
    [1, 2, 3]
    @. sqrt
end
```

は次のように等価です：

```julia
@chain begin
    [1, 2, 3]
    sqrt.(_)
end
```

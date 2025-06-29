```
@>>(first_arg, pipe::Expr)
```

`pipe`を無名関数に書き換え、`first_arg`をそれに渡します。`pipe`は`begin ... end`ブロックでなければなりません。`begin ... end`ブロック内の各行に対して関数が作成されます。前の関数の結果は次の関数に渡されます。

パイプは以下のルールに従って作成されます：

1. アンダースコアは関数引数として扱われます。`@>> [1,2,3] begin sum(_) end`は次と同等です。

`[1,2,3] |> x -> sum(x)`

2. 式にアンダースコアがない場合、最初の引数が入力されます。

`@>> [1,2,3] begin .+(3) end`は次と同等です。

`[1,2,3] |> x -> .+(x, 3)`

3. 式がシンボルの場合、それは関数として扱われます。したがって、`@>> "hello world" begin print end`は次のように解釈されます。

`"hello world" |> x -> print(x)`

4. 上記の2つのルールは、`begin end`ブロックの各行に適用されます。したがって、

```
    @>> 1 begin 
        [_, 1, 2] 
        sum()
    end
```

は`1 |> x -> [x, 1, 2] |> x -> sum(x)`と同等です。

5. これらのルールはマクロにも適用されますが、@>と@>>の例外があります。したがって、`@>> "hello world" begin @show end`

は`"hello world" |> x -> @show(x )`と同等です。

6. マクロは自己参照することもできます。@>>が自身の中に現れる場合、または@>とアンダースコアがパイプの最初の部分にある場合、それは周囲のコンテキストから来ます。以下の例を参照してください。
7. パイプ文字のシーケンス内にパイプ文字のシーケンスがある場合、最初の部分にアンダースコアが含まれていない場合、新しいパイプが作成されます。

`````
    @>> 1 begin  
        [_, 2, sqrt(36) |> _/2]
    end 
    
````
は`1 |> x -> [x, 3, sqrt(36) |> y -> y/2]`と同等です。

例：
`````

julia-repl julia> @>> 1 begin             [(@>> _ |> +(2)), 1, 1]              sum         end 5 ```

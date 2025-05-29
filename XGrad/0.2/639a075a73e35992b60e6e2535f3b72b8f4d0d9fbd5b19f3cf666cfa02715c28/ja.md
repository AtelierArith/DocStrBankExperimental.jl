```
xdiff(ex; ctx=Dict(), inputs...)
```

スカラー値の式をその入力に関して微分し、導関数の式を返します。

```
ex = :(sum(w * x .- y))
dex = xdiff(ex; w=rand(2,3), x=rand(3,4), y=rand(2))
```

`xdiff()` は、オプションを渡したり追加情報を抽出するために使用できるコンテキスト `ctx::Dict{Any,Any}` も受け入れます。いくつかのオプションには以下が含まれます：

  * `codegen::Espresso.CodeGen` - 導関数式に使用されるコード生成器；                               有効な値には `VecotorCodeGen()`, `BufCodeGen()`                               および `CuCodeGen()` が含まれます。

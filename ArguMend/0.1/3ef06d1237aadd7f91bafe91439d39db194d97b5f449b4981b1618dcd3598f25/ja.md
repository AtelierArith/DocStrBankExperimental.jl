```
@argumend [n_suggestions=3] [cutoff=0.6] funcdef
```

このマクロを使用すると、似たようなスペルのキーワードを自動的に提案できます：

```julia
@argumend function f(a, b; niterations=10, kw2=2)
    a + b - niterations + kw2
end
```

これにより、MethodErrorsのためのより良いメカニズムが得られます：

```julia
julia> f(1, 2; iterations=1)
ERROR: SuggestiveMethodError: in call to `f`, found unsupported
       keyword argument: `iterations`, perhaps you meant `niterations`
```

この関数は、誤って入力されたキーワード引数と他のすべてのキーワード引数との間の一致する部分列の最大数を数えることによって、近さを計算します。

マクロ内で指定することにより、提案の数をカスタマイズできます。また、`cutoff`を使用して近さの閾値を制御することもできます。

```
hcubature_buffer(f,a,b;norm=norm)
```

[`hcubature`](@ref)への呼び出しに使用できるバッファを割り当てます。引数 `(f,a,b;norm)` は、[`hcubature`](@ref) に渡されるものと同じです。

結果として得られるバッファは、エンドポイント `a,b` の*型*が同じであり、`f` の*戻り値の型*が変わらない限り、異なる *値* の `a,b` および `f` で再利用できます。

バッファを事前に割り当てることは、*類似* の引数 `f,a,b` に対して `hcubature` を何度も呼び出す予定がある場合にのみ有用であり、バッファの割り当て（および/または関連するガーベジコレクション）のコストが、積分の実際の評価に比べて重要である場合に限ります。

# 例:

```julia
f = x -> cos(x[1])*cos(x[2])
a,b = (0,0), (1,1)
buffer = hcubature_buffer(f,a,b)
I,E = hcubature(f,a,b; buffer=buffer)

# バッファは類似の呼び出しで再利用できます
g = x -> sin(x[1])*sin(x[2])
a,b = (0,0), (1.5,1.5)
I,E = hcubature(g,a,b; buffer=buffer)
```

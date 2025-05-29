```
assign!(e::AbstractExpr, assignment::Dict)
assign!(exprs::Array, assignment::Dict)
```

e内の式の値（ネストされた式や変数を含む）を、すべてのキーが式名に対応する文字列であり、対応する値がその満足する割り当てであるDictである`assignment`を使用して割り当てます。

`assign!`は、2つのケースで便利に使えることを意図しています。

1. インタラクティブモードで`sat!`によって返された`assignment`辞書を使用する場合。これは次のようになります：

```julia
    # いくつかのexprsを定義
    interactive_solver = open(solver)
    assert(interactive_solver, exprs...)
    status, assignment = sat!(interactive_solver)
    assign!.(exprs, assignment)
```

2. 生のSMT-LIB出力の"(get-model)"を解析する`parse_model`によって返された`assignment`辞書を使用する場合。

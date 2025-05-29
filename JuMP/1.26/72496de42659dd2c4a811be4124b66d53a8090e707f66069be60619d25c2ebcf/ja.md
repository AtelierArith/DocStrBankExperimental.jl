```
ComplexPlane
```

複素平面オブジェクトで、[`@variable`](@ref) マクロで複素変数を作成するために使用できます。

## 例

次の例を考えてみましょう：

```jldoctest
julia> model = Model();

julia> @variable(model, x in ComplexPlane())
real(x) + imag(x) im

julia> all_variables(model)
2-element Vector{VariableRef}:
 real(x)
 imag(x)
```

最後のコマンドの出力から、2つの実変数が作成されたことがわかります。Juliaの変数 `x` は、これら2つの変数に基づくアフィン式にバインドされ、複素平面をパラメータ化します。

```
add_derivative(model::InfiniteModel, d::Derivative, 
               [name::String = ""])::GeneralVariableRef
```

モデル `model` に導関数 `d` を追加し、それを指す `GeneralVariableRef` を返します。導関数の依存関係が `model` に属していない場合はエラーになります。`d` は、微妙な内部エラーを避けるために [`build_derivative`](@ref) を使用して構築する必要があります。

**例**

```julia-repl
julia> @infinite_parameter(m, t in [0, 1]); @variable(m, x, Infinite(t));

julia> info = VariableInfo(false, 0, false, 0, false, 0, false, 0, false, false);

julia> d = build_derivative(error, info, x, t);

julia> dref = add_derivative(m, d)
∂/∂t[x(t)]
```

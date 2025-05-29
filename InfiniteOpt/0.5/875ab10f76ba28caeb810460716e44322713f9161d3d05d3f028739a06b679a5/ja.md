```
JuMP.add_constraint(model::InfiniteModel, c::JuMP.AbstractConstraint,
                    [name::String = ""])::InfOptConstraintRef
```

`JuMP.add_constraint`を拡張して、無限モデル`model`に制約`c`を名前`name`で追加します。制約を定義するために使用される変数に応じて適切な制約参照を返します。変数が`model`に属していない場合はエラーを返します。これは主に制約マクロの内部メソッドとして使用されます。

**例**

```julia-repl
julia> @infinite_parameter(model, t in [0, 10]);

julia> @variable(model, g, Infinite(t));

julia> @variable(model, x);

julia> constr = build_constraint(error, g + x, MOI.EqualTo(42));

julia> cref = add_constraint(model, constr, "name")
name : g(t) + x = 42.0, ∀ t ∈ [0, 10]
```

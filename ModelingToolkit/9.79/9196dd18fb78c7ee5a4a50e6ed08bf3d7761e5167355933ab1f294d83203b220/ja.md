```julia
map_variables_to_equations(
    sys::ModelingToolkit.AbstractSystem;
    rename_dummy_derivatives
) -> Dict{Union{Symbolics.Num, SymbolicUtils.BasicSymbolic}, Symbolics.Equation}

```

`structural_simplify`を通じて簡略化されたシステムを考慮し、システムの変数をそれらを解決するために使用される方程式にマッピングする`Dict`を返します。これには観測された変数も含まれます。

# キーワード引数

  * `rename_dummy_derivatives`: ダミー導関数変数キーをその`Differential`形式に名前変更するかどうか。例えば、これはキー`yˍt(t)`を`Differential(t)(y(t))`に変換します。

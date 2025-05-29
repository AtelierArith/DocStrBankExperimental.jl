```
variable_dimensions(obj::AbstractCompositeComponentDef, comp_path::ComponentPath, var_name::Symbol)
```

`var_name`で指定された変数の次元の名前を、`obj`によって示される複合コンポーネント定義において、コンポーネントパス`comp_path`に沿って返します。`comp_path`は、複合ノードを通って特定の複合ノードまたはリーフノードへの相対的（複合に対して）または絶対的（ModelDefに対して）パスを説明するシンボルのNTupleからなる単一のフィールドを持つ`Mimi.ComponentPath`型です。

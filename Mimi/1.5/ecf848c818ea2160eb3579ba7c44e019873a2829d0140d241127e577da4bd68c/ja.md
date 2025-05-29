```
variable_dimensions(obj::AbstractCompositeComponentDef, comp::Symbol, var_name::Symbol)
```

コンポジットコンポーネント定義によって示される変数 `var_name` の次元の名前を返します。`comp_path` に沿ったコンポーネントパスを指定します。`comp_path` は、特定のコンポジットまたはリーフノードへのコンポジットノードを通る相対的（コンポジットに対して）または絶対的（ModelDefに対して）なパスを説明するシンボルのタプルです。

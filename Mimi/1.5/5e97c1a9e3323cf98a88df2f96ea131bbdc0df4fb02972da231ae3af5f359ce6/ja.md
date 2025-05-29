```
defcomp(comp_name::Symbol, ex::Expr)
```

Mimiコンポーネント`comp_name`を`ex`内の式で定義します。サポートされている式のタイプは次のとおりです：

1. `dimension_name = Index()`   # 次元を定義します
2. `parameter = Parameter(index = [dimension_name], units = "unit_name", default = default_value)`    # オプションの引数を持つパラメータを定義します
3. `variable = Variable(index = [dimension_name], units = "unit_name")`    # オプションの引数を持つ変数を定義します
4. `init(p, v, d)`              # コンポーネントの初期化関数を定義します
5. `run_timestep(p, v, d, t)`   # コンポーネントのrun_timestep関数を定義します

@defcomp定義を解析し、それを一連の関数呼び出しに変換して対応するComponentDefインスタンスを作成します。モデルビルド時に、ModelDef（そのComponentDefsを含む）は実行可能なモデルに変換されます。

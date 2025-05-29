```
processes_to_mtkmodel(processes::Vector [, default]; kw...)
```

提供された `processes` と `default` プロセスを使用して、ModelingToolkit.jl モデル/システムを構築します。モデル/システムは *構造的に簡略化されていません*。関数 [`processes_to_mtkeqs`](@ref) を使用して、生の `Vector{Equation}` を取得し、それを MTK モデル/システム（例えば `ODESystem`）に渡します。

構築中に、以下の自動化がユーザー体験を向上させます：

  * `processes` で導入された変数が自らプロセスを持たない場合、`default` からデフォルトプロセスを取得します。
  * デフォルトが存在しない場合でも、変数がデフォルトの数値値を持っている場合、該当する変数のために [`ParameterProcess`](@ref) が作成され、警告が表示されます。
  * それ以外の場合は、情報を含むエラーが表示されます。
  * 変数に二つ以上のプロセスが割り当てられている場合もエラーが表示されます。
  * 与えられたプロセスのいずれかが実際にはプロセスではなく、LHF変数を持たない式である場合もエラーが表示されます。

`processes` は以下の要素を持つ `Vector` です：

1. [`Process`](@ref) のサブタイプの任意のインスタンス。`Process` は `Equation` のラッパーのようなもので、時間スケールの処理や左辺形式（LHS）に制限がないなどの便利さを提供します。
2. `Equation`。方程式の LHS 形式には制限があります。`x` を `@variable`、`p` を `@parameter` とすると、LHS は次のいずれかでなければなりません：`x`、`Differential(t)(x)`、`Differential(t)(x)*p`、または `p*Differential(t)(x)`。`p` を含むバージョンは予期せず失敗する可能性があります。それ以外はエラーになります。
3. 上記の二つの `Vector` で、展開されます。これは、物理プロセスを表す関数が多くの方程式を定義する必要がある場合の便利さを提供します（例えば、より多くの変数を導入する可能性があるため）。
4. ModelingToolkit.jl の `XDESystem`。この場合、システムの `equations` は、上記のように方程式のベクトルとして与えられたかのように展開されます。これにより、既存の `XDESystem` と簡単に結合する便利さが得られます。

## デフォルトプロセス

`processes_to_mtkmodel` は、`default` を指定することでデフォルトプロセスを設定できます。これらのデフォルトプロセスは、メイン入力 `processes` で導入された変数に割り当てられますが、メイン入力にはプロセスが割り当てられていません。

`default` は、個々のプロセス（`Equation` または `Process`）の `Vector` であることができます。あるいは、`default` は `Module` であることもできます。ProcessBasedModelling.jl に基づく分野特有のモデリングライブラリを構築する推奨方法は、事前に定義された変数とプロセスのプールを提供するモジュール/サブモジュールを定義することです。モジュールは、関数 [`register_default_process!`](@ref) を介して独自のデフォルトプロセスを登録できます。これらの登録されたデフォルトプロセスは、`default` が `Module` の場合に使用されます。

## キーワード引数

  * `type = ODESystem`: 作成するモデルのタイプ。
  * `name = nameof(type)`: モデルの名前。
  * `independent = t`: 独立変数（デフォルト: `@variables t`）。`t` は便利のために ProcessBasedModelling.jl にもエクスポートされています。
  * `warn_default::Bool = true`: `true` の場合、変数に割り当てられたプロセスがないがデフォルト値があるときに警告を表示し、代わりにパラメータになることを示します。
  * `check_rhs::Bool = true`: `true` の場合、すべてのプロセスの RHS が `Equation` 型でないことを確認します。もしそうであれば、情報を含むエラーを表示します。これは、RHS が誤って LHS 自体を割り当てる `Equation` であるシナリオを助けます（私には何度も起こったことです！）。

```

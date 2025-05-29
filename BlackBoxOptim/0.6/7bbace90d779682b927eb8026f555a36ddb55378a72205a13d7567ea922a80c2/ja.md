```
bbsetup(problem[; parameters::Associative, kwargs...])
```

与えられた問題の最適化手法を設定します。

サポートされている`problem`のタイプについては`setup_problem()`を参照してください。最適化手法のパラメータは、`kwargs`または`parameters`引数を介して指定できます。

初期化された`OptController`インスタンスを返します。実際に手法を実行するには、`bboptimize()`または`run!()`を呼び出します。

サポートされているパラメータの完全なリストについては、[BlackBoxOptim.OptRunController](@ref)も参照してください。

```
code_ircode_by_mi(f, mi::MethodInstance; world=get_world_counter(), interp=NativeInterpreter(world))
```

`IRCode`オブジェクトと推論された戻り値の型を返します。

# 引数

  * `f(ir::IRCode, sv::OptimizationState) -> IRCode`: 実行する最適化パス。
  * `mi::MethodInstance`: メソッドインスタンス。

# キーワード引数

  * `world::Int`: ワールド番号、デフォルトは`Core.Compiler.get_world_counter`を呼び出すことです。
  * `interp::AbstractInterpreter`: 推論に使用するインタープリタ。

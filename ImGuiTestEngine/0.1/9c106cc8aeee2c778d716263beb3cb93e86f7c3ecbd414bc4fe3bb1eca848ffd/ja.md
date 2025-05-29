```julia
CreateContext(
;
    exit_on_completion,
    show_test_window
) -> ImGuiTestEngine.Engine

```

テストエンジンコンテキストを作成します。キーワード引数はこのライブラリでは何も機能しませんが、CImGui.jlのレンダーループでテストエンジンをサポートするために使用されます。

# 引数

  * `exit_on_completion=true`: テストが完了した後にプログラムを終了します。
  * `show_test_window=true`: テストを実行中に[`ShowTestEngineWindows()`](@ref)を呼び出します。

# 例

```julia
engine = te.CreateContext()
```

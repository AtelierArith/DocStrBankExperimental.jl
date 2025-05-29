```
@snoop_llvm "func_names.csv" "llvm_timings.yaml" begin
    # 実行するコマンド、新しいプロセスで
end
```

は、提供されたコマンドの間にLLVM最適化のタイミング情報をファイル "func*names.csv" と "llvm*timings.yaml" に記録するようにJuliaコンパイラに指示します。これらのファイルは、`SnoopCompile.read_snoop_llvm("func_names.csv", "llvm_timings.yaml")` への入力として使用できます。

ログには、各 "llvm モジュール" の最適化に費やされた時間と、モジュールに関する情報が含まれています。モジュールは、一緒に最適化される関数のコレクションです。

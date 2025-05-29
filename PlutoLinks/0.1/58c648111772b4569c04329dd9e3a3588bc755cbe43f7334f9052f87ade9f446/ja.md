```julia
	@use_process(command)::Nothing
```

コマンドを待機せずに実行し、呼び出しセルが明示的に実行されたときにプロセスを終了します。プロセスのstdoutおよびstderrの出力は、Plutoのログパネルに表示されます。

```julia
@PlutoLinks.use_process(`python -m http.server`)
```

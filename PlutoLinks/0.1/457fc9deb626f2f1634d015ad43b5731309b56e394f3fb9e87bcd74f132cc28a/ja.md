```julia
	@use_process_output(command)::IOBuffer
```

[`@use_process(command)`]()と似ていますが、プロセスのstdoutおよびstderr出力に結びついた`IOBuffer()`を返します。

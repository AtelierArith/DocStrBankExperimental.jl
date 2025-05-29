```julia
	@use_process(command)::Nothing
```

Executes the command without waiting and kills the process when the calling cell is explicitely executed. The stdout and stderr output of the process will show up in Pluto's log panel.

```julia
@PlutoLinks.use_process(`python -m http.server`)
```

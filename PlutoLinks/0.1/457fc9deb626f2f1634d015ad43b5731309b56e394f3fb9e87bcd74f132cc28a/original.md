```julia
	@use_process_output(command)::IOBuffer
```

Like [`@use_process(command)`]() but returns an `IOBuffer()` tied to the stdout and stderr output of the process.

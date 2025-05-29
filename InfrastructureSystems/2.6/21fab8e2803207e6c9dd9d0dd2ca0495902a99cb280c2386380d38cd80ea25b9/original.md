```julia
open_file_logger(func::Function, filename::String) -> Any
open_file_logger(
    func::Function,
    filename::String,
    level
) -> Any
open_file_logger(
    func::Function,
    filename::String,
    level,
    mode
) -> Any

```

Opens a file logger using `Logging.SimpleLogger`.

# Arguments

  * `func::Function`
  * `filename::String`: logger filename
  * `level=Logging.Info`: optional, to change the minimum logging level
  * `mode = "w+"`: Optional, to designate write mode

# Example

```Julia
open_file_logger("log.txt", Logging.Info) do logger
    global_logger(logger)
    @info "hello world"
end
```

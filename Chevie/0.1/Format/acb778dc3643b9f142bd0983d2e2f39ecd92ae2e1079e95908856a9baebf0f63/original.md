`rio(io::IO=stdout;p...)` enriches `io` with the attributes in `p`. It always enriches with `limit=true` to mimic display at the REPL.

Thus `print(rio(),x...)` is like printing `x...` at the REPL.

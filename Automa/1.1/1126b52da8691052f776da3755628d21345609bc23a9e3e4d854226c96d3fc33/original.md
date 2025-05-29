```
generate_reader(funcname::Symbol, machine::Automa.Machine; kwargs...)
```

Generate a streaming reader function of the name `funcname` from `machine`.

The generated function consumes data from a stream passed as the first argument and executes the machine with filling the data buffer.

This function returns an expression object of the generated function.  The user need to evaluate it in a module in which the generated function is needed.

# Keyword Arguments

  * `arguments`: Additional arguments `funcname` will take (default: `()`).   The default signature of the generated function is `(stream::TranscodingStream,)`,   but it is possible to supply more arguments to the signature with this keyword argument.
  * `context`: Automa's codegenerator (default: `Automa.CodeGenContext()`).
  * `actions`: A dictionary of action code (default: `Dict{Symbol,Expr}()`).
  * `initcode`: Initialization code (default: `:()`).
  * `loopcode`: Loop code (default: `:()`).
  * `returncode`: Return code (default: `:(return cs)`).
  * `errorcode`: Executed if `cs < 0` after `loopcode` (default error message)

See the source code of this function to see how the generated code looks like

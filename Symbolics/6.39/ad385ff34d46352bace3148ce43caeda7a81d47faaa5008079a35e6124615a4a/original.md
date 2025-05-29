```
build_function(ex, args...;
               expression = Val{true},
               target = JuliaTarget(),
               parallel=nothing,
               kwargs...)
```

Generates a numerically-usable function from a Symbolics `Num`.

Arguments:

  * `ex`: The `Num` to compile
  * `args`: The arguments of the function
  * `expression`: Whether to generate code or whether to generate the compiled form. By default, `expression = Val{true}`, which means that the code for the function is returned. If `Val{false}`, then the returned value is compiled.

Keyword Arguments:

  * `target`: The output target of the compilation process. Possible options are:

      * `JuliaTarget`: Generates a Julia function
      * `CTarget`: Generates a C function
      * `StanTarget`: Generates a function for compiling with the Stan probabilistic programming language
      * `MATLABTarget`: Generates an anonymous function for use in MATLAB and Octave environments
  * `parallel`: The kind of parallelism to use in the generated function. Defaults to `SerialForm()`, i.e. no parallelism, if `ex` is a single expression or an array containing <= 1500 non-zero expressions. If `ex` is an array of > 1500 non-zero expressions, then `ShardedForm(80, 4)` is used. See below for more on `ShardedForm`. Note that the parallel forms are not exported and thus need to be chosen like `Symbolics.SerialForm()`. The choices are:

      * `SerialForm()`: Serial execution.
      * `ShardedForm(cutoff, ncalls)`: splits the output function into sub-functions  which contain at most `cutoff` number of output `rhss`. These sub-functions  are called by the top-level function that *build*function returns.  This helps in reducing the compile time of the generated function.
      * `MultithreadedForm()`: Multithreaded execution with a static split, evenly splitting the number of expressions per thread.
  * `fname`: Used by some targets for the name of the function in the target space.

Note that not all build targets support the full compilation interface. Check the individual target documentation for details.

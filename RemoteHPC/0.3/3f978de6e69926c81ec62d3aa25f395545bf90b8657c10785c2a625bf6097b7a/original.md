```
Exec(;name::String = "",
      path::String = "",
      flags::Dict = Dict(),
      modules::Vector{String} = String[],
      parallel::Bool = true)
```

Representation of an executable. As with any [`Storable`](@ref), `name` is used simply as a label to be able to [`load`](@ref) it from the [`Server`](@ref) where it is stored.

In a job script this will be translated as `<path> <flags>`.

# `configure()` Example

```julia
name::String = "exec_label"
path::String = "/path/to/exec"
flags::Dict{Any, Any} = Dict{Any, Any}("l" => 1, "-np" => 4, "trialname" => "testtrial")
modules::Vector{String} = String["intel","intel-mkl"]
parallel::Bool = false
```

# Example:

```julia
Exec(; path="ls", flags=Dict("l" => ""))
```

translates into `ls -l` in the jobscript.

# Flags

The `flags` `Dict` is expanded into the jobscript as follows:

```julia
Exec(path="foo", flags = Dict("N"    => 1,
                              "-nk"  => 10,
                              "np"   => "$NPOOLS",
                              "--t"  => "",
                              "--t2" => 24)
# translates into: foo -N1 -nk 10 --np=$NPOOLS --t --t2=24
```

# Modules

The `modules` vector gets expanded into `module load` commands: `modules = ["gcc", "QuantumESPRESSO"]` will lead to `module load gcc, QuantumESPRESSO` in the jobscript.

# Parallel

`parallel` communicates whether the executable should be ran with the parallel executable defined in the [`Environment`](@ref) that represents the execution environment. For example:

```julia
# If the Environment of the job is defined as:
Environment(parallel_exec=Exec(path="srun"))
# then the follow Exec:
Exec(path="foo", parallel=true)
# wille be translated into: srun foo
```

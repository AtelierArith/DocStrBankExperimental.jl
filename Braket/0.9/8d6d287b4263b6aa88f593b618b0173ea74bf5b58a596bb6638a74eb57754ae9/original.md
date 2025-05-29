```
IRType
```

A `Ref{Symbol}` which records which IR output format to use by default. Currently, two formats are supported:

  * `:JAQCD`, the Amazon Braket IR
  * `:OpenQASM`, the OpenQASM3 representation

By default, `IRType` is initialized to use `:OpenQASM`, although this may change in the future. The current default value can be checked by calling `IRType[]`. To change the default IR format, set `IRType[]`.

# Examples

```jldoctest
julia> IRType[]
:OpenQASM

julia> IRType[] = :JAQCD;

julia> IRType[]
:JAQCD

julia> IRType[] = :OpenQASM;
```

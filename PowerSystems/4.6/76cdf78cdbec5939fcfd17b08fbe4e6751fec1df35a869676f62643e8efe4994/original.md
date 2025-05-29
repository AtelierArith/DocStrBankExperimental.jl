```julia
System(
    sys_file::AbstractString,
    dyr_file::AbstractString;
    kwargs...
) -> Any

```

Parse static and dynamic data directly from PSS/e text files. Automatically generates all the relationships between the available dynamic injection models and the static counterpart

Each dictionary indexed by id contains a vector with 5 of its components:

  * Machine
  * Shaft
  * AVR
  * TurbineGov
  * PSS

Files must be parsed from a .raw file (PTI data format) and a .dyr file.

## Examples:

```julia
raw_file = "Example.raw"
dyr_file = "Example.dyr"
sys = System(raw_file, dyr_file)
```

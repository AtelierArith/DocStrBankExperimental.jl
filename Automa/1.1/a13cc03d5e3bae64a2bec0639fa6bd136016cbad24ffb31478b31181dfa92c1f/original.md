```
machine2dot(machine::Machine)::String
```

Return a String with a flowchart of the machine in Graphviz (dot) format. Using `Graphviz`, a command-line tool, the dot file can be converted to various picture formats.

# Example

```julia
open("/tmp/machine.dot", "w") do io
    println(io, machine2dot(machine))
end
# Requires graphviz to be installed
run(pipeline(`dot -Tsvg /tmp/machine.dot`), stdout="/tmp/machine.svg")
```

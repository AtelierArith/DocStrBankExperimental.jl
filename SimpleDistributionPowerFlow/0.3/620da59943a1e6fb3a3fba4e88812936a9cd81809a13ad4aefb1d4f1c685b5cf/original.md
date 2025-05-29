```
gridtopology(;kwargs...)
```

A `function` that discover the network topology by analizing the input data. 

It presents two topology graphs: one based on raw input data (input topology), and other (working topology)  based on specific characteristics such as distributed loads and open or closed switches. The working topology is the topology used by `powerflow()` function.

Data is input via `.cvs` files with minimum specification, there is not need to indicate midpoints for distributed loads,  `gridtopology()` automatically creates dummy buses in the middle of line segments to simulate distributed loads.

Even it can display the topology graph without x,y bus position information.

# Keyword arguments

```jldoctest
    input::String=""
    output::String=""
    save_topology::Bool=true
    display_topology::Bool=false
    display_topology::Bool=false
    graph_title::String=""
    marker_size::Float64=1.5
    timestamp::Bool=false
```

# Data files

Following files must be in the input directory:

```jldoctest
    substation.csv
    line_segments.csv
    line_configurations.csv
```

Following files must be in the input directory if needed:

```jldoctest
    transformers.csv
    regulators.csv
    switches.csv
    distributed_loads.csv
```

Following file is optional: `bus_coords.csv`

There are other files required by `powerflow()` function but they are not required by `gridtopology()` operation.

# Notes

Use `input="somewhere"` to specify the directory where input files are. If the directory does not exists `gridtopology()`  warns it and stop execution.

Use `output="somewhere"` to specify the directory where input results will be written. If the directory does not exists  it will be created by `gridtopology()`.

By default `gridtopology()` does not show the topology graph in computer screen, in order to automatically display it `gridtopology(display_topology=true)` is needed.

You can change some graphics attributes such as the graph title, marker size and timestamp. Keyword arguments must be separated by commas.

# Example:

```jldoctest
gridtopology(input="examples/ieee-34", output="results", display_topology=true, graph_title="ieee 34 node test feeder", marker_size=12, timestamp=true)
```

Here `gridtopology()` discover the topology of the network specified by configuration files located in relative directory examples/ieee-34. Two png image files will be saved in the directory named results, their filenames will have a sufix with the date-hour-minute of creation. Topology images will also be displayed on screen with the specified title. The bus indicator circle marker will have a relative size of 12. 

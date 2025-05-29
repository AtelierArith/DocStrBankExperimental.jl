```
powerflow(;kwargs...)
```

A `function` to evaluate the voltage levels of a three-phase distribution network and the power  flow in lines between buses based on grid infrastructure, loads and generation information.    

Data is input via `.cvs` files with minimum specification. There is not need to indicate midpoints for distributed  loads, or sequential enumeration of buses, `powerflow()` leverages on `gridtopology()` to discover the  network topology. It can evaluate bus voltages and reversing power flows due change in topology by opening and closing switches.

# Keyword arguments

```jldoctest
    input::String=""
    output::String=""
    tolerance::Float64=1e6
    max_iterations::Int=30
    display_summary::Bool=true
    save_topology::Bool=false
    display_topology::Bool=false
    graph_title::String=""
    marker_size::Float64=1.5
    timestamp::Bool=false
    verbose::Bool=0
```

# Data files

Following files must be in the input directory:

```jldoctest
    substation.csv
    line_segments.csv
    line_configurations.csv
    spot_loads.csv
```

Following files must be in the input directory if needed:

```jldoctest
    transformers.csv
    regulators.csv
    switches.csv
    capacitors.csv
    distributed_loads.csv
    distributed_generation.csv
```

Following file is optional: `bus_coords.csv`

# Notes

By default `powerflow()` reads input files from, and writes result files to the current directory. Is user want to load files from other directory must specify with the input argument, also if he/she want to save result files to other directory must be specified whith output argument.

By default a resume of total input and loss power, and the result of buses voltages  are displayed in computer screen after execution, the other results are saved in .csv files in output directory.

The result files can have a timestamp for sequencial analysis. 

Currently `powerflow()` only works with radial feeders, the user can change the state of  switches in order to open loops if presented. 

The operational algorithm is based on forward-backward sweeps, with the generalized matrices proposed by William H. Kersting in Distribution System Modeling and Analysis, 4th ed, Taylor & Francis Group 2017.

# Example:

```jldoctest
powerflow(input="examples/ieee-34", output="results", tolerance=1e-9, max_iterations=30, display_topology=true, 
          graph_title="ieee 34 node test feeder", marker_size=12, timestamp=true)
```

Here `powerflow()`, by internally calling `gridtopology()` function display on terminal's screen the topology of the network specified  and executes the forward and backward sweeps until the calculated substation voltage differs lower than 1e-9 from the original value or 30 iterations are reached.

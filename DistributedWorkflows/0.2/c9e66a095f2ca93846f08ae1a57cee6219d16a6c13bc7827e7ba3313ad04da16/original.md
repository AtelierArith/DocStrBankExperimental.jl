```
show_workflow(pnet::Workflow_PetriNet)
```

Converts the given Petri net object to an SVG string and displays it as HTML to the screen. This functionality is meant to be used within environments like IJulia.jl or Pluto.jl, not the REPL.

# Arguments

  * `pnet::Workflow_PetriNet`: Petri net object describing the workflow to visualize

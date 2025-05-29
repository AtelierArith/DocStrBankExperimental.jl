```
connect(systems, connections; external_inputs, external_outputs = (:), verbose = true, unique = true, kwargs...)
```

Create block connections using named inputs and outputs.

Addition and subtraction nodes are achieved by creating a linear combination node, i.e., a system with a `D` matrix only.

# Arguments:

  * `systems`: A vector of named systems to be connected
  * `connections`: a vector of pairs output => input, where each pair maps an output to an input. Each output must appear as an output in one of `systems`, and similarly each input must appear as an input in one of `systems`. All inputs must have unique names and so must all outputs, but an input may have the same name as an output. In the example below the connection `:uP => :uP` connects the output `:uP` of the `addP` block to `P`'s input `:uP`
  * `external_inputs`: external signals to be used as inputs in the constructed system. Use `(:)` to indicate all signals
  * `external_outputs`: outputs of the constructed system. Use `(:)` to indicate all signals
  * `verbose`: Issue warnings for signals that have no connection
  * `unique`: If `true`, all input names must be unique. If `false`, a single external input signal may be connected to multiple input ports with the same name.

Note: Positive feedback is used, controllers that are intended to be connected with negative feedback must thus be negated.

Example: The following complicated feedback interconnection

```
                 yF
               ┌────────────────────────────────┐
               │                                │
    ┌───────┐  │  ┌───────┐        ┌───────┐    │    ┌───────┐
uF  │       │  │  │       | yR     │       │ yC │ uP │       │   yP
────►   F   ├──┴──►   R   │────+───►   C   ├────+────►   P   ├───┬────►
    │       │     │       │    │   │       │         │       │   │
    └───────┘     └───────┘    │   └───────┘         └───────┘   │
                               │                                 │
                               └─────────────────────────────────┘
```

can be created by

```
F = named_ss(ssrand(1, 1, 2, proper=true), x=:xF, u=:uF, y=:yF)
R = named_ss(ssrand(1, 1, 2, proper=true), x=:xR, u=:uR, y=:yR)
C = named_ss(ssrand(1, 1, 2, proper=true), x=:xC, u=:uC, y=:yC)
P = named_ss(ssrand(1, 1, 3, proper=true), x=:xP, u=:uP, y=:yP)

addP = sumblock("uP = yF + yC") # Sum node before P
addC = sumblock("uC = yR - yP") # Sum node before C

connections = [
    :yP => :yP # Output to input
    :uP => :uP
    :yC => :yC
    :yF => :yF
    :yF => :uR
    :uC => :uC
    :yR => :yR
]
external_inputs = [:uF] # External inputs

G = connect([F, R, C, P, addP, addC], connections; external_inputs)
```

If an external input is to be connected to multiple points, use a `splitter` to split up the signal into a set of unique names which are then used in the connections.

```
dep(m::ModelList, nsteps=1; verbose::Bool=true)
dep(mapping::Dict{String,T}; verbose=true)
```

Get the model dependency graph given a ModelList or a multiscale model mapping. If one graph is returned,  then all models are coupled. If several graphs are returned, then only the models inside each graph are coupled, and the models in different graphs are not coupled. `nsteps` is the number of steps the dependency graph will be used over. It is used to determine the length of the `simulation_id` argument for each soft dependencies in the graph. It is set to `1` in the case of a  multiscale mapping.

# Details

The dependency graph is computed by searching the inputs of each process in the outputs of its own scale, or the other scales. There are five cases for every model (one model simulates one process):

1. The process has no inputs. It is completely independent, and is placed as one of the roots of the dependency graph.
2. The process needs inputs from models at its own scale. We put it as a child of this other process.
3. The process needs inputs from another scale. We put it as a child of this process at another scale.
4. The process needs inputs from its own scale and another scale. We put it as a child of both.
5. The process is a hard dependency of another process (only possible at the same scale). In this case, the process is set as a hard-dependency of the

other process, and its simulation is handled directly from this process.

For the 4th case, the process have two parent processes. This is OK because the process will only be computed once during simulation as we check if both  parents were run before running the process. 

Note that in the 5th case, we still need to check if a variable is needed from another scale. In this case, the parent node is  used as a child of the process at the other scale. Note there can be several levels of hard dependency graph, so this is done recursively.

How do we do all that? We identify the hard dependencies first. Then we link the inputs/outputs of the hard dependencies roots  to other scales if needed. Then we transform all these nodes into soft dependencies, that we put into a Dict of Scale => Dict(process => SoftDependencyNode). Then we traverse all these and we set nodes that need outputs from other nodes as inputs as children/parents. If a node has no dependency, it is set as a root node and pushed into a new Dict (independant*process*root). This Dict is the returned dependency graph. And  it presents root nodes as independent starting points for the sub-graphs, which are the models that are coupled together. We can then traverse each of  these graphs independently to retrieve the models that are coupled together, in the right order of execution.

# Examples

```@example
using PlantSimEngine

# Including example processes and models:
using PlantSimEngine.Examples;

models = ModelList(
    process1=Process1Model(1.0),
    process2=Process2Model(),
    process3=Process3Model(),
    status=(var1=15.0, var2=0.3)
)

dep(models)

# or directly with the processes:
models = (
    process1=Process1Model(1.0),
    process2=Process2Model(),
    process3=Process3Model(),
    process4=Process4Model(),
    process5=Process5Model(),
    process6=Process6Model(),
    process7=Process7Model(),
)

dep(;models...)
```

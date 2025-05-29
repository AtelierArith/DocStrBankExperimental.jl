```julia
struct EnsembleSplitThreads <: SciMLBase.BasicEnsembleAlgorithm
```

A mixture of distributed computing with threading. The optimal version of this is to have a process on each node of a computer and then multithread on each system. However, this ensembler will simply use the node setup provided by the Julia Distributed processes, and thus it is recommended that you setup the processes in this fashion before using this ensembler. See Julia's Distributed documentation for more information

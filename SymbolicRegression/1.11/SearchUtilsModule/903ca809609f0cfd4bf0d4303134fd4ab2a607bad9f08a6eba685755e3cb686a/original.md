```
SearchState{T,L,N,WorkerOutputType,ChannelType} <: AbstractSearchState{T,L,N}
```

The state of the search, including the populations, worker outputs, tasks, and channels. This is used to manage the search and keep track of runtime variables in a single struct.

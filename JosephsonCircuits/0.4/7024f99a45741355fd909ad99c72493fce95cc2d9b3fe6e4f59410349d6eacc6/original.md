```
connectS(networks, connections; small_splitters::Bool = true,
    nbatches::Int = Base.Threads.nthreads())
```

Return the network and ports resulting from connecting the networks in `networks` according to the connections in `connections`. `networks` is a vector of tuples of the network name and scattering parameter matrix such as [("network1name",rand(Complex{Float64},2,2), ("network2name",rand(Complex{Float64},2,2)]. `connections` is a vector of vectors of tuples of networks names and ports such as [[("network1name",1), ("network2name",2)]] where network1 and network2 are the two networks being connected and 1 and 2 are integers describing the ports to connect.

This function supports connections between more than two ports by automatically adding splitters.

# Examples

```jldoctest
networks = [("S1",[0.0 1.0;1.0 0.0]),("S2",[0.5 0.5;0.5 0.5])];
connections = [[("S1",1),("S2",2)]];
JosephsonCircuits.connectS(networks,connections)

# output
(S = [[0.5 0.5; 0.5 0.5]], ports = [[("S1", 2), ("S2", 1)]])
```

```jldoctest
networks = [("S1",[0.0 1.0;1.0 0.0]),("S2",[0.5 0.5;0.5 0.5],[("S3",5),("S3",6)])];
connections = [("S1","S3",1,6)];
JosephsonCircuits.connectS(networks,connections)

# output
(S = [[0.5 0.5; 0.5 0.5]], ports = [[("S1", 2), ("S3", 5)]])
```

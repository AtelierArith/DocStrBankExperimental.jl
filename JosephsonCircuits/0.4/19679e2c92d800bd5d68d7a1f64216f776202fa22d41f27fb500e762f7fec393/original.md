```
solveS(networks, connections; small_splitters::Bool = true,
    factorization = KLUfactorization(), internal_ports::Bool = false,
    nbatches::Integer = Base.Threads.nthreads())
```

Perform the connections between the networks in `networks` specified by the vector of vectors of tuples `connections`. Return the sparse matrix of scattering parameters for the external ports `S` and the external ports `ports`. Also return the internal port scattering parameters `Sinternal` and the internal ports `portsinternal`.

# Arguments

  * `networks`: a vector of tuples of the network name, scattering parameter   matrix, and optionally the ports  such as   [("network1name",rand(Complex{Float64},2,2))] or   [("S1",[0.0 1.0;1.0 0.0]),("S2",[0.5 0.5;0.5 0.5])].
  * `connections::AbstractVector{<:AbstractVector{Tuple{T,Int}}}`: a vector of   vectors of tuples of networks names and ports such as [[("S1",1),("S2",2)]]   or [[("network1name",1),("network2name",2)]] where network1 and network2   are the two networks being connected and 1 and 2 are integers describing   the ports to connect.

# Keywords

  * `small_splitters::Bool = true`: if true, then generate any N port splitter   by combining (N-2) 3 port splitters. if false, then make the N port   splitter and connect the components to it.
  * `factorization = KLUfactorization()`: use KLU factorization by default.    JosephsonCircuits.LUfactorization() is another good choice. Keyword   arguments can be passed to the solver as keyword arguments to these   functions.
  * `internal_ports::Bool = false`: return the scattering parameters for the   internal ports.
  * `nbatches::Integer = Base.Threads.nthreads()`: the number of batches to run   on threads. Defaults to the number of threads with which Julia was   launched.

# Returns

  * `S`: sparse matrix of scattering parameters for the external ports.
  * `ports`: the vector of tuples of network name and port number for the   external ports.
  * `Sinternal`: sparse matrix of scattering parameters for the internal ports.
  * `portsinternal`: the vector of tuples of network name and port number for the   internal ports.

# Examples

```jldoctest
networks = [("S1",[0.0 1.0;1.0 0.0]),("S2",[0.5 0.5;0.5 0.5])];
connections = [[("S1",1),("S2",2)]];
JosephsonCircuits.solveS(networks,connections;internal_ports=true)

# output
(S = [0.5 0.5; 0.5 0.5], ports = [("S1", 2), ("S2", 1)], Sinternal = [1.0 0.0; 0.5 0.5], portsinternal = [("S1", 1), ("S2", 2)])
```

```jldoctest
networks = [("S1",[0.0 1.0;1.0 0.0]),("S2",[0.5 0.5;0.5 0.5],[("S3",5),("S3",6)])];
connections = [("S1","S3",1,6)];
JosephsonCircuits.solveS(networks,connections)

# output
(S = [0.5 0.5; 0.5 0.5], ports = [("S1", 2), ("S3", 5)], Sinternal = Float64[], portsinternal = [("S1", 1), ("S3", 6)])
```

# References

V. A. Monaco and P. Tiberio, "Computer-Aided Analysis of Microwave Circuits," in IEEE Transactions on Microwave Theory and Techniques, vol. 22, no. 3, pp. 249-263, Mar. 1974, doi: 10.1109/TMTT.1974.1128208.

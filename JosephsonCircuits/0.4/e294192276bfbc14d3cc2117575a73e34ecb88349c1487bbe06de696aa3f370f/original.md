```
connectS(Sa::AbstractArray, k::Int, l::Int;
    nbatches::Int = Base.Threads.nthreads())
```

Connect ports `k` and `l` on the same `m` port microwave network represented by the scattering parameter matrix `Sa`, resulting in an `(m-2)` port network, as illustrated below:

Input network:

```
      m |         | l+1    
        |   ...   |         l
        |_________|__________ 
        |         |          |
        |   Sa    |  ...     |
        |  m x m  |          |
    ____|_________|_____ k+1 |
    1   |   ...   |          |
        |         | k        |
      2 |         |__________|
```

Output network:

```
    m-2 |         | l-1     
        |         |         
        |   ...   |         
        |_________|         
        |         |         
        |    S    |  ...    
        |m-2 x m-2|         
    ____|_________|_________
    1   |   ...         k   
        |                   
        |                   
      2 |                   
```

# Arguments

  * `Sa::Array`: Array of scattering parameters representing the network   with ports along first two dimensions, followed by an arbitrary number   of other dimensions (eg. frequency).
  * `k::Int`: First port to connect, with one based indexing.
  * `l::Int`: Second port to connect, with one based indexing.

# References

V. A. Monaco and P. Tiberio, "Computer-Aided Analysis of Microwave Circuits," in IEEE Transactions on Microwave Theory and Techniques, vol. 22, no. 3, pp. 249-263, Mar. 1974, doi: 10.1109/TMTT.1974.1128208.

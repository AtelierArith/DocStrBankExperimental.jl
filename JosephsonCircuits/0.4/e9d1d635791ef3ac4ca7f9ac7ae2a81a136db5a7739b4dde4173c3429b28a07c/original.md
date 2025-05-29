```
connectS(Sa::AbstractArray,Sb::AbstractArray,k::Int,l::Int;
    nbatches::Int = Base.Threads.nthreads())
```

Connect port `k` on an `m` port network, represented by the scattering parameter matrix `Sa`, to port `l` on an `n` port network, represented by the scattering parameter matrix `Sb`, resulting in a single `(m+n-2)` port network, as illustrated below:

Input network:

```
      m |        | k+1                       | 2
        |        |                           |
        |   ...  |                     ...   |
        |________|                  _________|________
        |        |                  |        |       1
        |   Sa   |                  |   Sb   |
        |  m x m |                  |  n x n |
    ____|________|__________________|________|
    1   |   ...     k           l   |   ...  |
        |                           |        |
        |                           |        |
      2 |                       l+1 |        | n
```

Output network:

```
    m-1 |        | k      | m+1    
        |        |        |        
        |   ...  |   ...  |        
        |________|________|________
        |                 |     m  
        |        S        |        
        |  m+n-2 x m+n-2  |        
    ____|_________________|        
    1   |   ...  |   ...  |        
        |        |        |        
        |        |        |        
      2 |        |        |  m+n-2 
                m-1+l              
```

# Arguments

  * `Sa::Array`: Array of scattering parameters representing the first network   with ports along first two dimensions, followed by an arbitrary number   of other dimensions (eg. frequency).
  * `Sb::Array`: Array of scattering parameters representing the second network   with ports along first two dimensions, followed by an arbitrary number   of other dimensions (eg. frequency).
  * `k::Int`: Port on first network, with one based indexing.
  * `l::Int`: Port on second network, with one based indexing.

# References

V. A. Monaco and P. Tiberio, "Computer-Aided Analysis of Microwave Circuits," in IEEE Transactions on Microwave Theory and Techniques, vol. 22, no. 3, pp. 249-263, Mar. 1974, doi: 10.1109/TMTT.1974.1128208.

```
est_1st_order_markov_bg(vec_str::Vector{Sting}; laplace=1; F=FloatType)

Estimate the Markov matrix, e.g.,
        A   C   G   T       
    A  0.1 0.3 0.4 0.2 
    C  0.5 0.1 0.1 0.3
    G  0.2 0.2 0.2 0.4
    T  0.7 0.1 0.1 0.1
in the (shuffled) background sequence.
The rows and the columns are ordered in A, C, G, T.

And estimate the initial distribution, e.g,
    A   C   G   T       
   0.2 0.2 0.3 0.3 
The columns are ordered in A, C, G, T.
```

Input:

  * `vec_str`: vector of strings
  * `laplace`: pseudocounts to add (optional, default to 1)
  * `F`: datatype of the estiamtes (optional, default to Float32)

Output:     The estimated 4x4 markov matrix and 4x1 initial distribution.

σ(d::AbstractVector, cup::UnionSetArray; [algorithm]="support_vector")

Return a support vector of the union of a finite number of sets in a given direction.

### Input

  * `d`         – direction
  * `cup`       – union of a finite number of sets
  * `algorithm` – (optional, default: "support*vector"): the algorithm to compute                the support vector; if "support*vector", use the support                vector of each argument; if "support_function", use the support                function of each argument and evaluate the support vector of                only one of them

### Output

A support vector in the given direction.

### Algorithm

The support vector of the union of a finite number of sets $X₁, X₂, ...$ can be obtained as the vector that maximizes the support function, i.e., it is sufficient to find the $\argmax([ρ(d, X₂), ρ(d, X₂), ...])$ and evaluate its support vector.

The default implementation, with option `algorithm="support_vector"`, computes the support vector of all $X₁, X₂, ...$ and then compares the support function using the dot product.

If the support function can be computed more efficiently, the alternative implementation `algorithm="support_function"` can be used, which evaluates the support function of each set directly and then calls only the support vector of one of the $Xᵢ$.

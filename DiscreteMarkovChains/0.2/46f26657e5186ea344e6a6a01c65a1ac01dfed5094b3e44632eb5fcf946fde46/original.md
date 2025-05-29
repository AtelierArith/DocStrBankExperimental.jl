```
decompose(x)
```

All transition matrices can be reordered so that we have

$$
T = \begin{pmatrix}
A & 0\\
B & C
\end{pmatrix}
$$

Where $A$, $B$ and $C$ are as described below. $0$ is a matrix of zeros.

# Arguments

  * `x`: some kind of Markov chain.

# Returns

A tuple of four values

  * `states`: the first value is an array of the new states.
  * `A`: the second value is a matrix of recurrent states to recurrent states.
  * `B`: the third value is a matrix of transient states to recurrent states.
  * `C`: the fourth value is a matrix of transient to transient states.

# Examples

```jldoctest decompose
using DiscreteMarkovChains
T = [
    0.0 1.0 0.0;
    1.0 0.0 0.0;
    0.1 0.2 0.7;
]
X = DiscreteMarkovChain(["Sunny", "Cloudy", "Rainy"], T)

decompose(X)

# output

(Any["Sunny", "Cloudy", "Rainy"], [0.0 1.0; 1.0 0.0], [0.1 0.2], [0.7])
```

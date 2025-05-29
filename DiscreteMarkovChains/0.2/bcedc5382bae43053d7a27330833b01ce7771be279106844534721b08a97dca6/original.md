```
periodicities(x::AbstractDiscreteMarkovChain)
```

A more advanced version of `communication_classes` designed for discrete Markov chains. It is the same as `communication_classes` but it returns periodicities as well.

# Definitions

The period, $d_i$ of a state $i$ is the greatest common denominator of all integers $n ∈ \mathbb{N}$ for which $p^{(n)}_{i,i} > 0$. Written more succinctly,

$$
d_i = \text{gcd}\{ n ∈ \mathbb{N} | p^{(n)}_{i,i} > 0 \}
$$

If $d_i=1$ then state $i$ is said to be aperiodic.

# Arguments

  * `x`: some kind of discrete Markov chain.

# Returns

A tuple containing 3 arrays.

  * This first array contains C arrays which store the states that communicate.
  * The second array is an array of Bool where the ith value is true if the ith communication class is recurrent.
  * The third array is the periodicity of each communication class.

# Examples

```jldoctest periodicities
using DiscreteMarkovChains
T = [
    1 0;
    0 1;
]
X = DiscreteMarkovChain(T)

periodicities(X)

# output

([[1], [2]], Any[true, true], Any[1, 1])
```

So the Markov chain has two communication classes and both are recurrent and aperiodic.

```jldoctest periodicities
T = [
    0.0 1.0 0.0;
    1.0 0.0 0.0;
    0.1 0.2 0.7;
]
X = DiscreteMarkovChain(["Sunny", "Cloudy", "Rainy"], T)

periodicities(X)

# output

([["Sunny", "Cloudy"], ["Rainy"]], Any[true, false], Any[2, 1])
```

So the Sunny and Cloudy states communicate and are recurrent with period 2. The Rainy state is transient and aperiodic. Note that this is not a very good weather model since once it stops raining, it will never rain again. Also, each day after that, the process will oscillate between Sunny and Cloudy.

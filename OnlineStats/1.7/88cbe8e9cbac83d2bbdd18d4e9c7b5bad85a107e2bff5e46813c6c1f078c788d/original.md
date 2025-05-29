```
HyperLogLog(T = Number)
HyperLogLog{P}(T = Number)
```

Approximate count of distinct elements of a data stream of type `T`, using `2 ^ P` "registers".  `P` must be an integer between 4 and 16 (default).

By default it returns the improved HyperLogLog cardinality estimator as defined by [1].

The original HyperLogLog estimator [2] can be retrieved with the option `original_estimator=true`.

# Example

```
o = HyperLogLog()
fit!(o, rand(1:100, 10^6))

using Random
o2 = HyperLogLog(String)
fit!(o2, [randstring(20) for i in 1:1000])

# by default the improved estimator is returned:
value(o)
# the original HyperLogLog estimator can be retrieved via:
value(o; original_estimator=true)
```

# References

[1] Improved estimator: Otmar Ertl. New cardinality estimation algorithms for HyperLogLog sketches. [https://arxiv.org/abs/1702.01284](https://arxiv.org/abs/1702.01284)

[2] Original estimator: P. Flajolet, Éric Fusy, O. Gandouet, and F. Meunier. Hyperloglog: The analysis of a near-optimal cardinality estimation algorithm. *In Analysis of Algorithms (AOFA)*, pages 127–146, 2007.

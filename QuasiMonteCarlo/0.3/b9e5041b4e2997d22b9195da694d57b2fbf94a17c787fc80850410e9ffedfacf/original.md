```
VanDerCorputSample(base::Integer, R::RandomizationMethod = NoRand()) <: DeterministicSamplingAlgorithm
```

The van der Corput sequence, also called the radical inverse sequence, is a one-dimensional low-discrepancy sequence that recursively splits the unit interval into equally-sized pieces before inserting one sample in each interval.

For example, in base 2, the sequence starts by inserting one point in each half of the unit interval in the first pass (the first 2 samples); then one sample in each quarter, then each eighth, and so on. This creates a well-stratified sample, so long as the number of samples is a multiple of a power of the base.

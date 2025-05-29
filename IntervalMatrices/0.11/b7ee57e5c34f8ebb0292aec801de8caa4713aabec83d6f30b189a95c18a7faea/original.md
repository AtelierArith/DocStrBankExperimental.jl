```
increment(pow::IntervalMatrixPower; [algorithm=default_algorithm])
```

Increment a matrix power without modifying `pow`.

### Input

  * `pow` – wrapper of a matrix power
  * `algorithm` – (optional; default: `default_algorithm`) algorithm to compute                the matrix power; see [`increment!`](@ref) for available options

### Output

The next matrix power.

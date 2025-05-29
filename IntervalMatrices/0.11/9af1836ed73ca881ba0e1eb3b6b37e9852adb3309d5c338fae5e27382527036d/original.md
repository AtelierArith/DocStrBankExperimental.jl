```
increment!(pow::IntervalMatrixPower; [algorithm=default_algorithm])
```

Increment a matrix power in-place (i.e., storing the result in `pow`).

### Input

  * `pow`       – wrapper of a matrix power (modified in this function)
  * `algorithm` – (optional; default: `default_algorithm`) algorithm to compute                the matrix power; available options:

      * `"multiply"` – fast computation using `*` from the previous result
      * `"power"` – recomputation using `^`
      * `"decompose_binary"` – decompose `k = 2a + b`
      * `"intersect"` – combination of `"multiply"`/`"power"`/`"decompose_binary"`

### Output

The next matrix power, reflected in the modified wrapper.

### Notes

Independent of `"algorithm"`, if the index is a power of two, we compute the exact result using squaring.

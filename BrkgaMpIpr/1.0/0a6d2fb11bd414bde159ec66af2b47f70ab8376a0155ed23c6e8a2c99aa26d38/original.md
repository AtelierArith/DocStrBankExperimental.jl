```
@enum ShakingType
```

Specifies the type of shaking to be performed.

  * `CHANGE`: applies the following perturbations:

    1. Inverts the value of a random chosen, i.e., from `value` to `1 - value`;
    2. Assigns a random value to a random key.
  * `SWAP`: applies two swap perturbations:

    1. Swaps the values of a randomly chosen key `i` and its neighbor `i + 1`;
    2. Swaps values of two randomly chosen keys.

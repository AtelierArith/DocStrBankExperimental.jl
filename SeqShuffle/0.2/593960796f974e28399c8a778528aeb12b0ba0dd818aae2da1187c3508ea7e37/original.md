```
seq_shuffle(seq::String; k=2, seed=nothing)
```

Shuffle the input string such that it preserves the frequency of k-mers

Input:

  * `seq`: A string
  * `k`: interger; k-mer frequency
  * `seed`: (integer) seed for random number generation

Output:     A shuffled version of the input string `seq`

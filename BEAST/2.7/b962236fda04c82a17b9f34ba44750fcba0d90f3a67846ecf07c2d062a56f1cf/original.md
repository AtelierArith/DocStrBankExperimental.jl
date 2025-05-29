```
blockassembler(operator, test_space, trial_space) -> assembler
```

Return a callable object for the creation of blocks within a BEM matrix.

This function performs all tasks common to the assembly of several blocks within a single boundary element matrix. The return value can be used to generate blocks by calling it as follows:

```
assembler(I,J,storefn)
```

where `I` and `J` are arrays of indices in `test_space` and `trial_space`, respectively, corresponding to the rows and columns of the desired block.

Note that the block will be constructed in compressed form, i.e. the rows and columns of the store that are written into are the positions within `I` and `J` (as opposed to the positions within `1:numfunctions(test_space)` and `1:numfunctions(trial_space)`). In particular the size of the constructed block will be `(length(I), length(J))`.

This last property allows the assembly of permutations of the BEM matrix by supplying for `I` and `J` permutations of `1:numfunctions(test_space)` and `1:numfunctions(trial_space)`.

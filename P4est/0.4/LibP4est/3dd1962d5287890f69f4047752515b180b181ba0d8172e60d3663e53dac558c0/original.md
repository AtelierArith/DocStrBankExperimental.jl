```
sc_array_permute(array, newindices, keepperm)
```

Given permutation *newindices*, permute *array* in place. The data that on input is contained in *array*[i] will be contained in *array*[newindices[i]] on output. The entries of newindices will be altered unless *keepperm* is true.

### Parameters

  * `array`:[in,out] An array.
  * `newindices`:[in,out] Permutation array (see [`sc_array_is_permutation`](@ref)).
  * `keepperm`:[in] If true, *newindices* will be unchanged by the algorithm; if false, *newindices* will be the identity permutation on output, but the algorithm will only use O(1) space.

### Prototype

```c
void sc_array_permute (sc_array_t * array, sc_array_t * newindices, int keepperm);
```

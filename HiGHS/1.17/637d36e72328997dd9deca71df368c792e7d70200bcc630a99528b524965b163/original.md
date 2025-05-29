```
Highs_deleteRowsByMask(highs, mask)
```

Delete multiple rows given by a mask.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `mask`: An array of length [num_row] with `1` if the row should be deleted and `0` otherwise. The new index of any column not deleted is stored in place of the value `0`.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.

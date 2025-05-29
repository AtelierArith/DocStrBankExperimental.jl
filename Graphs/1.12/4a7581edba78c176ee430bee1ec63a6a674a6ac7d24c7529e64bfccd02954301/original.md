```
prufer_decode(code)
```

Returns the unique tree associated with the given (Prüfer) code.  Each tree of size n is associated with a Prüfer sequence (a[1], ..., a[n-2]) with 1 ⩽ a[i] ⩽ n. The sequence is constructed recursively by the leaf removal algoritm. At step k, the leaf with smallest index is removed and its unique neighbor is added to the Prüfer sequence, giving a[k]. The decoding algorithm goes backward.  The tree associated with the empty sequence is the 2-vertices tree with one edge. Ref: [Prüfer sequence on Wikipedia](https://en.wikipedia.org/wiki/Pr%C3%BCfer_sequence)

```
unfold(vf::VectorFold; from=1, to=folds(vf))
```

Construct the unfolded version of `vf` (with the same type as `pattern(vf)`) based. Please note that using an iterator on `vf` avoid memory allocation, which is not the case of `unfold`.

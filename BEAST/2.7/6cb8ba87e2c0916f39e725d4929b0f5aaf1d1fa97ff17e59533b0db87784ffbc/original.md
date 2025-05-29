```
ntrace(refspace, element, localindex, face)
```

Compute the normal trace of all local shape functions on `elements` belonging to `refspace` on `face`. This function returns a matrix expressing the traces of local shape functions in `refspace` as linear combinations of functions in the local trace space. Cf. `restrict`. `localindex` is the index of `face` in the enumeration of faces of `elements`. In many special cases knowing this index allows for highly optimised implementations.

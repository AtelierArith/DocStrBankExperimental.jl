```
FlexIx{I}(indices)
```

For `fi = FlexIx{I}(indices)`:

  * indexing `a[fi]` is equivalent to `a[indices]`;
  * `@set a[fi] = vs` works even for `vs` of different length than `indices`, shortening/lengthening `a` as needed.

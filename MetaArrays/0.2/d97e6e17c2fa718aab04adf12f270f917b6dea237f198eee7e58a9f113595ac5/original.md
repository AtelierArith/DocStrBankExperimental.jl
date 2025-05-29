```
MetaArray(meta::A, array)
```

Create a meta array with custom metadata type `A`.

Normally it's recommended that you use `meta`; only use a custom meta-data type if you plan to have a method specialize on the second type argument of the MetaArray.

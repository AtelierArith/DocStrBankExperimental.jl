```
sc_recycle_array
```

The [`sc_recycle_array`](@ref) object provides an array of slots that can be reused.

It keeps a list of free slots in the array which will be used for insertion while available. Otherwise, the array is grown.

```
key_submap_iterable = get_submaps_shallow(choices::ChoiceMap)
```

Return an iterator over tuples of the form `(key, submap::ChoiceMap)` for each top-level key that has a non-empty sub-assignment.

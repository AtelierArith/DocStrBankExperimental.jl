```
copy_facts(from_kb::AbstractReteRootNode, to_kb::AbstractReteRootNode, fact_types)
```

Copues facts if the specified `fact_type` from `from_kb` to `to_kb`.

for multiple fact types, one can broadcast over a collection of fact types.

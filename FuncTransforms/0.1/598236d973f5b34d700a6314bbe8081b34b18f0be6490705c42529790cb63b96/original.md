```
assignva!(fi::FuncInfo, varid::Union{SlotNumber, Int}, vaid::Union{SlotNumber, Int}, index::Integer)
```

Add the code at the beginning of code block that: given the new vararg (`vaid`),  extract the element at `index and assign to the old argument`varid`.

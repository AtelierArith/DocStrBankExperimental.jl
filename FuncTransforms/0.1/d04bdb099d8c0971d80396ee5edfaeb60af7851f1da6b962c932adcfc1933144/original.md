```
repackva!(fi::FuncInfo, varid::Union{SlotNumber, Int}, vaid::Union{SlotNumber, Int}, indices::Vector{Integer})
```

Add the code at the beginning of code block that: given the new vararg (`vaid`),  extract the element at `indices`, pack them as a tuple and assign to the old vararg (`varid`).

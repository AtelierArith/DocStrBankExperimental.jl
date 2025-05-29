```
unsafe_to_pointer
```

!!! warning
    `val`がグローバルにルートされており、それへのポインタが漏洩する可能性があることを前提としています。`pointer_from_objref`を優先してください。Enzyme.jl内でのみ、Typesのために使用してください。


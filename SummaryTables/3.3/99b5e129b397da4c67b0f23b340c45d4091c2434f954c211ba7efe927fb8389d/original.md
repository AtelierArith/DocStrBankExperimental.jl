```
Annotated(value, annotation; label = AutoNumbering())
```

Create an `Annotated` object which will be given a footnote annotation in the `Table` where it is used. If the `label` keyword is `AutoNumbering()`, annotations will be given number labels from 1 to N in the order of their appearance. If it is `nothing`, no label will be shown. Any other `label` will be used directly as the footnote label.

Each unique label must be paired with a unique annotation, but the same combination can exist multiple times in a single table.

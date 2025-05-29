```
recurrence_threshold(rt::AbstractRecurrenceType, x [, y] [, metric]) → ε
```

Return the calculated distance threshold `ε` for `rt`. The output is real, unless `rt isa LocalRecurrenceRate`, where `ε isa Vector`.

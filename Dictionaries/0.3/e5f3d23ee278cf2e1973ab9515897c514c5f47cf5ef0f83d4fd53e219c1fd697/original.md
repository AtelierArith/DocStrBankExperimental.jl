```
insert!(dict::AbstractDictionary, i, value)
```

Insert the `value` at new index `i` into `dict`. An error is thrown if index `i` already exists.

Hint: Use `setindex!` to update an existing value, and `set!` to perform an "upsert" (update-or-insert) operation.

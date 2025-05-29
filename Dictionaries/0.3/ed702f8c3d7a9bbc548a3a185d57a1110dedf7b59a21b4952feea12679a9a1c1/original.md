```
set!(dict::AbstractDictionary, i, value)
```

Update or insert the `value` at index `i` into `dict`. Sometimes referred to as an "upsert" operation.

Hint: Use `setindex!` to exclusively update an existing value, and `insert!` to exclusively insert a new value. See also `get!`.

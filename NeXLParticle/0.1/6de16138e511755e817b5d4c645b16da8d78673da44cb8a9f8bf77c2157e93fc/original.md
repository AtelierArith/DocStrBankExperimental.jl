```
separate(b::Blob, concavity = 0.42, withinterior = true)::Vector{Blob}
```

Break b into many Blob(s) by looking for concave regions on the perimeter and joining them with a short(ish) line.

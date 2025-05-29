```
@either true ? "right" : Symbol("left")
@either if false
  "right"
else
  :left
end
```

Simple macro to reuse ? operator and simple if-else for constructing Either.

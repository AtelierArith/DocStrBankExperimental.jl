```
Secret(name::AbstractString)
```

Represents a GitHub repository secret. When converted to a string, yields `${{ secrets.<name> }}`.

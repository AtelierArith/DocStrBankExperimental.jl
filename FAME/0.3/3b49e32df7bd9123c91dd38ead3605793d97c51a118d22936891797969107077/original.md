```
workdb()
```

Return a [`FameDatabase`](@ref) instance for the work database. 

Since the work database can be open only once, we create an instance the first time and return the existing instance each subsequent time.

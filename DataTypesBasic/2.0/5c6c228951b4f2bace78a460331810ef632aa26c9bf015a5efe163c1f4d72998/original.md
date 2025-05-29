```
@ContextManager function(cont); ...; end
```

There is a simple `@ContextManager` for writing less parentheses

```julia
mycontextmanager(value) = @ContextManager function(cont)
  println("got value = $value")
  result = cont(value)
  println("finished value = $value")
  result
end
```

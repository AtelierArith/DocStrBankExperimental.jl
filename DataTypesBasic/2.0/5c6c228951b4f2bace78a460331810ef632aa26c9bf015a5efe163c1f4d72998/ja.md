```
@ContextManager function(cont); ...; end
```

単純な `@ContextManager` があり、括弧を少なく書くことができます。

```julia
mycontextmanager(value) = @ContextManager function(cont)
  println("got value = $value")
  result = cont(value)
  println("finished value = $value")
  result
end
```

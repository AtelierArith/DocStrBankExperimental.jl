`@with resources... block` Produces code like:

```
let resources...
   try
       block
   finally
       close.(resources)
   end
end
```

This is useful for resources implementing `Base.close` but no callbacked resource opener.

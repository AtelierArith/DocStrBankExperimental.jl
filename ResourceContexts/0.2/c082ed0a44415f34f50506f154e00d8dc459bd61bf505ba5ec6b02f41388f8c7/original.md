```
@! enter_do(func, args...)
```

`enter_do` transforms do-block-based resource management into context-based resource management. That is, if the user is expected to write

```
func(args...) do x,y
    # do stuff with x,y
end
```

they can instead use `func` with a context, as in

```
x,y = @! enter_do(func, args...)
```

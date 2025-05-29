```
@with! df begin
    # do something with df
end
```

The `@with!` macro is a convenience macro that allows you to set the current data frame and perform operations on it in a single block. The first argument is the data frame to set as the current data frame, and the second argument is a block of code to execute. The data frame is set as the current data frame for the duration of the block, and then restored to its previous value after the block is executed.

The macro does not have a return value, it overwrites the data frame directly.

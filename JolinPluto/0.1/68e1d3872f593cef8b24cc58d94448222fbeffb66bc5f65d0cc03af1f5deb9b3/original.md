```
channel = @Channel(10) do ch
    for i in 1:10
        put!(ch, i)
        sleep(1)
    end
end
```

Like normal `Channel`, with the underlying task being interrupted as soon as the Pluto cell is deleted.

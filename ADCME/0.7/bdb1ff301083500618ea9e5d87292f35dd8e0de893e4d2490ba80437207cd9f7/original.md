```
change_directory(directory::Union{Missing, AbstractString})
```

Change the current working directory to `directory`. If `directory` does not exist, it is made. 

If `directory` is missing, the default is `ADCME.PREFIXDIR`.

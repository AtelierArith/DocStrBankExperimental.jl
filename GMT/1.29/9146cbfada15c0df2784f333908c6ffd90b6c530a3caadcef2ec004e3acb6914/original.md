```
gmtmath(cmd::String, args...)
```

Call gmtmath with all commands in a single string 'cmd'. This is not useful in itself as compared to call gmt("gmtmath ....") but it's very useful in 'movie' because it can generate shell scripts from the julai command

See full GMT (not the `GMT.jl` one) docs at [`grdmath`](http://docs.generic-mapping-tools.org/latest/grdmath.html)

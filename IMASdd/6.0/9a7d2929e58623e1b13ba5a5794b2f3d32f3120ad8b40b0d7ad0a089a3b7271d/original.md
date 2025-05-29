```
@ddtime( X.Y )
```

Get data from time dependent array. Equivalent to:

```
get_time_array(X, :Y)
```

and

```
@ddtime( X.Y = V)
```

Set data in a time dependent array. Equivalent to:

```
set_time_array(X, :Y, V)
```

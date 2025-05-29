Construct polynomial variables and bind them to local variables of the same name. Usage:

Create a single variable named x:

```
@polyvar(x)
```

Create several variables at the same time:

```
@polyvar(x, y, z)
```

Create a tuple of variables x = (x1, x2, x3, x4):

```
@polyvar(x[1:4])
```

Create variables x, y, a = (a1, a2, a3):

```
@polyvar(x, y, a[1:3])
```

You can also assign the results of the macro to a tuple:

```
vars = @polyvar(x[1:5])
@assert typeof(vars[1]) == Variable{:x1}
```

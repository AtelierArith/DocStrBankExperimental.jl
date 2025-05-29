```
@ptconf(expr...)
```

Add configurations in `expr` to be used with the macro `@pt`.

The expression format must be:

```
keyword1 = value1 keyword2 = value2 ...
```

in which the keywords can be any other possible keyword that can be used in the function `pretty_table`.

!!! warning
    If a keyword is not supported by the function `pretty_table`, then no error message is printed when calling `@ptconf`. However, an error will be thrown when `@pt` is called.


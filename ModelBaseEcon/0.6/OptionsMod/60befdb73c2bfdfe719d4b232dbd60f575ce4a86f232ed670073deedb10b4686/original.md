```
setoption!(o::Options; name=default [, name=default, ...])
setoption!(o::Options, name, default)
```

Retrieve the value of an option or a set of options. If the name does not match an existing option, the Options instance is updated by inserting the given name and default value.

The return value is the value of the option requested (or the default). In the first version of the function, if there are more than one options requested, the return value is a tuple.

In the second version, the name could be a symbol or a string, which can be helpful if the name of the option is not a valid identifier.

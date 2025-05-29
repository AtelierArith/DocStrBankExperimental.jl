```
man(obj::T)
man(obj::Symbol)
```

Prints a long text that explains what `obj` generally is in computer programming and how it is implemented in the Julia programming language. Note that `T` can only be a Julia stdlib type or a composite type that is a subtype of a Julia stdlib type. If a type that does not meet these requirements is used, an error will be thrown.

Examples of using `man` can be found in the docstrings of `REPLference`, using the `help?>` mode.

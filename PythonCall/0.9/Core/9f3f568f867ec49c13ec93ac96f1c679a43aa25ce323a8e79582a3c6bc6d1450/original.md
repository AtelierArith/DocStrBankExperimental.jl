```
pytype(name, bases, dict)
```

Create a new type. Equivalent to `type(name, bases, dict)` in Python.

If `bases` is not a Python object, it is converted to one using `pytuple`.

The `dict` may either by a Python object or a Julia iterable. In the latter case, each item may either be a `name => value` pair or a Python object with a `__name__` attribute.

In order to use a Julia `Function` as an instance method, it must be wrapped into a Python function with [`pyfunc`](@ref PythonCall.pyfunc). Similarly, see also [`pyclassmethod`](@ref PythonCall.pyclassmethod), [`pystaticmethod`](@ref PythonCall.pystaticmethod) or [`pyproperty`](@ref PythonCall.pyproperty). In all these cases, the arguments passed to the function always have type `Py`. See the example below.

# Example

```julia
Foo = pytype("Foo", (), [
    "__module__" => "__main__",

    pyfunc(
        name = "__init__",
        doc = """
        Specify x and y to store in the Foo.

        If omitted, y defaults to None.
        """,
        function (self, x, y = nothing)
            self.x = x
            self.y = y
            return
        end,
    ),

    pyfunc(
        name = "__repr__",
        self -> "Foo($(self.x), $(self.y))",
    ),

    pyclassmethod(
        name = "frompair",
        doc = "Construct a Foo from a tuple of length two.",
        (cls, xy) -> cls(xy...),
    ),

    pystaticmethod(
        name = "hello",
        doc = "Prints a friendly greeting.",
        (name) -> println("Hello, $name"),
    ),

    "xy" => pyproperty(
        doc = "A tuple of x and y.",
        get = (self) -> (self.x, self.y),
        set = function (self, xy)
            (x, y) = xy
            self.x = x
            self.y = y
            nothing
        end,
    ),
])
```

`mv2dir(f::Function, srcfile, newdir::AbstractString)` moves a file `srcfile` to a directory `newdir`. The new path for the `srcfile` is `newpath = joinpath(newdir, basename(srcfile)) |> f`, where an arbitrary function `f` can be applied to the `newpath`.

`mv2dir` takes keyword arguments of `mv`.

# Examples

`mkdirway(newpath)` makes directories along the way to the file `newpath`:

```julia
mv2dir(mkdirway, "hello/world/iris.csv", "another/world") # results in "another/world/iris.csv"
```

which is equivualent to:

```julia
mkpath("another/world")
mv2dir("hello/world/iris.csv", "another/world") # results in "another/world/iris.csv"
```

If `srcfile` is a directory,

```julia
mkpath("another") # noted that "another/world" not created
mv2dir("hello/world", "another") # Move all contents under "world" to the new folder "another", resulting in "another/world/iris.csv"
```

which is equivualent to

```julia
mv2dir(mkdirway, "hello/world", "another") # results in "another/world/iris.csv"
```

Also see the docstring of `mkdirway`.

# Another example

You can apply `f = pathnorepeat` that

```julia
mv2dir(pathnorepeat, "hello/world", "another") # results in "another/world_0001/iris.csv" if directory "another/world" already exists.

mv2dir(pathnorepeat, "hello/world/iris.csv", "another/world") # results in "another/world/iris_0001.csv" if file "another/world/iris.csv" already exists.
```

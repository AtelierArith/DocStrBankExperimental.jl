```julia
File{T <: Any} <: Servable
```

  * name**::String**
  * path**::String**

The `File` `Servable` writes a file to a `Connection`. `T` will be the file extension  of the file, meaning a `.html` file becomes a `File{:html}`. Getting index on a file, `File[]`,  will yield the field path. Using `string` on a file will read the file as a `String`.

```julia
File(`dir`**::String**)
```

```example
# write! candidate
io = IOBuffer()

# make a file
myf::File{:jl} = File("myfiles/example.jl")
# writing
write!(io, myf)
```

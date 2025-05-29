```
import_off_file(fname)
```

Import a file in OFF (Object File Format).

Returns a Tuple - vertices, and faces. Vertices is a vector of [x, y, z], and faces a vector of vectors of vertex numbers. 

```julia
off_file = raw"
    OFF
    8 6 0
    -0.500000 -0.500000 0.500000
    0.500000 -0.500000 0.500000
    -0.500000 0.500000 0.500000
    0.500000 0.500000 0.500000
    -0.500000 0.500000 -0.500000
    0.500000 0.500000 -0.500000
    -0.500000 -0.500000 -0.500000
    0.500000 -0.500000 -0.500000
    4 0 1 3 2
    4 2 3 5 4
    4 4 5 7 6
    4 6 7 1 0
    4 1 7 5 3
    4 6 0 2 4
"

f = open("/tmp/cube.off", "w") do f
    write(f, off_file)    
end

@draw begin
    o = make(import_off_file("/tmp/cube.off"))
    scaleby!(o, 100)
    pin(o)
end
```

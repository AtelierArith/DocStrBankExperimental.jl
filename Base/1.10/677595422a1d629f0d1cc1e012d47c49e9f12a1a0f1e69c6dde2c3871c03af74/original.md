Construct an uninitialized Pipe object.

The appropriate end of the pipe will be automatically initialized if the object is used in process spawning. This can be useful to easily obtain references in process pipelines, e.g.:

```
julia> err = Pipe()

# After this `err` will be initialized and you may read `foo`'s
# stderr from the `err` pipe.
julia> run(pipeline(pipeline(`foo`, stderr=err), `cat`), wait=false)
```

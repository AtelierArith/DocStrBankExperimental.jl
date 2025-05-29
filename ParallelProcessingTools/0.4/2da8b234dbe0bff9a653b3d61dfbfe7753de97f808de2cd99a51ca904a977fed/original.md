```
function read_files(
    [f_read, ], filenames::AbstractString...;
    use_cache::Bool = true, cache_dir::AbstractString = default_cache_dir(),
    create_cachedir::Bool = true, delete_tmp_onerror::Bool=true,
    verbose::Bool = false
)
```

Reads `filenames` in an atomic fashion (i.e. only if all `filenames` exist) on a best-effort basis (depending on the OS and file-system used).

If a reading function `f_read` is given, calls `f_read(filenames...)`. The return value of `f_read` is passed through.

If `use_cache` is `true`, then the files are first copied to the cache directory `cache_dir` under temporary names, and then read via `f_read(temporary_filenames...)`. The temporary files are deleted after `f_read` exits (except if an exception is thrown during reading and `delete_tmp_onerror` is set to `false`).

Set `ENV["JULIA_DEBUG"] = "ParallelProcessingTools"` to see a log of all intermediate steps.

For example:

```julia
write("foo.txt", "Hello"); write("bar.txt", "World")

result = read_files("foo.txt", "bar.txt", use_cache = true) do foo, bar
    read(foo, String) * " " * read(bar, String)
end
```

If no reading funcion `f_read` is given, then `read_files` returns an object of type [`FilesToRead`](@ref) that holds the temporary filenames. Closing it will clean up temporary files, like described above. So

```julia
ftr = read_files("foo.txt", "bar.txt"; use_cache = true)
result = try
    foo, bar = collect(ftr)
    data_read = read(foo, String) * " " * read(bar, String)
    close(ftr)
    data_read
catch err
    close(ftr, err)
    rethrow()
end
```

is equivalent to the example using `read_files(f_read, ...)`above.

If `create_cachedir` is `true`, then `cache_dir` will be created if it doesn't exist yet.

If `verbose` is `true`, uses log-level `Logging.Info` to log file reading, otherwise `Logging.Debug`.

On Linux you can set `use_cache = true` and `cache_dir = "/dev/shm"` to use the default Linux RAM disk as an intermediate directory.

See also [`write_files`](@ref) and [`ParallelProcessingTools.default_cache_dir`](@ref).

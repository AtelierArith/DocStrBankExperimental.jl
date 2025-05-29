```
function write_files(
    [f_write,] filenames::AbstractString...;
    mode::WriteMode = CreateOrIgnore(),
    use_cache::Bool = false, cache_dir::AbstractString = default_cache_dir(),
    create_dirs::Bool = true, delete_tmp_onerror::Bool=true,
    verbose::Bool = false
)
```

Writes to `filenames` in an atomic fashion, on a best-effort basis (depending on the OS and file-system used).

`mode` determines how to handle pre-existing files, it may be [`CreateOrIgnore()`](@ref) (default), [`CreateNew()`](@ref), [`CreateOrReplace()`](@ref), [`CreateOrModify()`](@ref) or [`ModifyExisting()`](@ref).

If a writing function `f_write` is given, calls `f_create(temporary_filenames...)`. If `f_create` doesn't throw an exception, the files `temporary_filenames` are renamed to `filenames`, otherwise the temporary files are are either deleted (if `delete_tmp_onerror` is `true) or left in place (e.g. for debugging purposes).

Set `ENV["JULIA_DEBUG"] = "ParallelProcessingTools"` to see a log of all intermediate steps.

For example:

```julia
write_files("foo.txt", "bar.txt", use_cache = true) do tmp_foo, tmp_bar
    write(tmp_foo, "Hello")
    write(tmp_bar, "World")
end
```

`write_files(f_write, filenames...)` returns either `filenames`, if the files were (re-)written or `nothing` if there was nothing to do (depending on `mode`).

If no writing funcion `f_write` is given then, `write_files` returns an object of type [`FilesToWrite`](@ref) that holds the temporary filenames. Closing it will, like above, either rename temporary files to `filenames` or remove them. So

```julia
ftw = write_files("foo.txt", "bar.txt")
if !isnothing(ftw)
    try
        foo, bar = ftw
        write(foo, "Hello")
        write(bar, "World")
        close(ftw)
    catch err
        close(ftw, err)
        rethrow()
    end
end
```

is equivalent to the example using `write_files(f_write, ...)`above.

When modifying files, `write_files` first copies existing files `filenames` to `temporary_filenames` and otherwise behaves as described above.

If `use_cache` is `true`, the `temporary_filenames` are located in `cache_dir` and then atomically moved to `filenames`, otherwise they located next to `filenames` (so in the same directories).

If `create_dirs` is `true`, target and cache directory paths are created if necessary.

If `verbose` is `true`, uses log-level `Logging.Info` to log file creation, otherwise `Logging.Debug`.

On Linux you can set `use_cache = true` and `cache_dir = "/dev/shm"` to use the default Linux RAM disk as an intermediate directory.

See also [`read_files`](@ref) and [`ParallelProcessingTools.default_cache_dir`](@ref).

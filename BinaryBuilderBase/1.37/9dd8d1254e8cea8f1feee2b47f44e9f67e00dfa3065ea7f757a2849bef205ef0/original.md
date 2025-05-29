A `LibraryProduct` is a special kind of [`Product`](@ref) that not only needs to exist, but needs to be `dlopen()`'able.  You must know which directory the library will be installed to, and its name, e.g. to build a `LibraryProduct` that refers to `"/lib/libnettle.so"`, the "directory" would be "/lib", and the "libname" would be "libnettle".  Note that a `LibraryProduct` can support multiple libnames, as some software projects change the libname based on the build configuration.

---

```
LibraryProduct(libname, varname::Symbol, dir_paths=String[];
               dont_dlopen=false, dlopen_flags=Symbol[])
```

Declares a `LibraryProduct` that points to a library located within the prefix. `libname` specifies the basename of the library, `varname` is the name of the variable in the JLL package that can be used to call into the library.  By default, the library is searched in the `libdir`, but you can add other directories within the prefix to the `dir_paths` argument.  You can specify the flags to pass to `dlopen` as a vector of `Symbols` with the `dlopen_flags` keyword argument.  If the library should not be dlopen'ed automatically by the JLL package, set `dont_dlopen=true`.

For example, if the `libname` is `libnettle`, this would be satisfied by the following paths:

  * `lib/libnettle.so` or `lib/libnettle.so.6` on Linux and FreeBSD;
  * `lib/libnettle.6.dylib` on macOS;
  * `lib/libnettle-6.dll` on Windows.

Libraries matching the search pattern are rejected if they are not `dlopen()`'able.

If you are unsure what value to use for `libname`, you can use `Base.BinaryPlatforms.parse_dl_name_version`:

```
julia> using Base.BinaryPlatforms

julia> parse_dl_name_version("sfml-audio-2.dll", "windows")[1]
"sfml-audio"
```

If the library would have different basenames on different operating systems (e.g., `libz.so` on Linux and FreeBSD, `libz.dylib` on macOS, and `zlib.dll` on Windows), `libname` can be also a vector of `String`s with the different alternatives:

```
LibraryProduct(["libz", "zlib"], :libz)
```

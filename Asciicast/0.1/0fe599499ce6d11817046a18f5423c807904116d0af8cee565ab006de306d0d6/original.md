```
cast_readme(MyPackage::Module)
cast_readme(MyPackage::Module, output_path)
```

Add gifs for each `julia {cast="true"}` code-block in the README of MyPackage. This is just a smaller helper that calls [`cast_document`](@ref) on `joinpath(pkgdir(MyPackage), "README.md")`. See [`cast_document`](@ref) for more options and warnings.

```
cast_readme(MyPackage::Module)
cast_readme(MyPackage::Module, output_path)
```

MyPackageのREADME内の各 `julia {cast="true"}` コードブロックに対してGIFを追加します。これは、[`cast_document`](@ref) を `joinpath(pkgdir(MyPackage), "README.md")` に対して呼び出す小さなヘルパーです。詳細なオプションや警告については、[`cast_document`](@ref) を参照してください。

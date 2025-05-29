```
build_app_bundle(juliaprog_main;
    appname, builddir, binary_name, resources, libraries, verbose, bundle_identifier,
    app_version, icns_file, certificate, entitlements_file, snoopfile, autosnoop,
    commandline_app, cpu_target)
```

`juliaprog_main`を実行可能ファイルにコンパイルし、すべての`resources`と`libraries`を含むAppを`appname`という名前でバンドルします。

juliaprog*main: `julia*main()`関数を定義する".jl"ファイルへのパス

# 例

```julia-repl
julia> build_app_bundle("main.jl", appname="MyApp", resources=["img.jpg"],
           libraries=[MyPackage._libp])
```

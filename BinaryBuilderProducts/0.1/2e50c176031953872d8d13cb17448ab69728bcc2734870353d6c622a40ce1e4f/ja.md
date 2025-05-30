```
ExecutableProduct(names::Vector{String}, varname::Symbol; dir_path = nothing)
```

すべてのプラットフォームで、`ExecutableProduct`はファイルの存在を確認します。Windowsプラットフォームでは、ファイルが".exe"で終わることを確認し、（すでに存在しない場合は自動的に検索パスに追加します）。

```
locate(ep::ExecutableProduct, prefix::String;
       verbose::Bool = false)
```

指定された実行可能ファイルが存在し、実行可能である場合、そのパスを返します。

すべてのプラットフォームで、[`ExecutableProduct`](@ref) はファイルの存在を確認します。非Windowsプラットフォームでは、実行可能ビットが設定されているかどうかを確認します。Windowsプラットフォームでは、ファイルが ".exe" で終わるかどうかを確認し、既に存在しない場合は自動的に追加します。

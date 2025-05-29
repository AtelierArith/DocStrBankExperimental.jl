```
set_libceed_path!(path::AbstractString)
set_libceed_path!(:prebuilt)
set_libceed_path!(:default)
```

libCEED動的ライブラリのパスを設定します。`path`はライブラリファイルへの絶対パスである必要があります。

`set_libceed_path!(:prebuilt)`は、LibCEED.jlにlibCEEDライブラリのプリビルド版（libCEED_jllにバンドルされている）を使用することを示します。

`set_libceed_path!(:default)`は、LibCEED.jlにデフォルトのライブラリを使用することを示します。これは通常、`set_libceed_path!(:prebuilt)`と同じ効果がありますが、デポ全体の設定や[Overrides.toml](https://pkgdocs.julialang.org/dev/artifacts/#Overriding-artifact-locations)を使用して異なるパスが指定されている場合を除きます。

この関数は、現在アクティブな環境に関連付けられた*設定*としてライブラリパスを設定します。変更はJuliaセッションを再起動した後に有効になります。詳細については、[Preferences.jlのドキュメント](https://github.com/JuliaPackaging/Preferences.jl)を参照してください。

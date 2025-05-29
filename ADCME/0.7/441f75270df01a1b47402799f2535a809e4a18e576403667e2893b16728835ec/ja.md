```
get_library(filename::AbstractString)
```

有効なライブラリファイルを返します。例えば、`filename = "adcme"` の場合、次のようになります。

  * MacOSでは、関数は `libadcme.dylib` を返します
  * Linuxでは、関数は `libadcme.so` を返します
  * Windowsでは、関数は `adcme.dll` を返します

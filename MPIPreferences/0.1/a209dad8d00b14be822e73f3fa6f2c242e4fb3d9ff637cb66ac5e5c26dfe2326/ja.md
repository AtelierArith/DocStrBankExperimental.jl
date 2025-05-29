```
use_jll_binary([binary]; export_prefs=false, force=true)
```

JLLパッケージによって提供される基盤となるMPI実装に切り替えます。変更を有効にするにはJuliaの再起動が必要です。

利用可能なオプションは次のとおりです：

  * `"MicrosoftMPI_jll"`（唯一のオプションで、Windowsのデフォルト）
  * `"MPICH_jll"`（他のすべてのプラットフォームのデフォルト）
  * `"OpenMPI_jll"`
  * `"MPItrampoline_jll"`

`export_prefs`オプションは、設定される優先設定が`LocalPreferences.toml`または`Project.toml`内に保存されるべきかどうかを決定します。

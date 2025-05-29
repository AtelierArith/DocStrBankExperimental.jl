```
locate(fp::FileProduct, prefix::Prefix;
       platform::AbstractPlatform = HostPlatform(),
       verbose::Bool = false,
       isolate::Bool = false)
```

指定されたファイルが存在する場合、そのパスを返します。`platform`および`isolate`引数はここでは無視されますが、一貫性のために含まれています。使いやすさのために、`${target}`や`${nbits}`のような限られた数のカスタム変数展開をサポートしており、`/lib32/i686-linux-musl`のようなターゲット固有のフォルダー内のファイルの検出が簡単になります。

```
enable_nan_injection(n_inject::Int)
```

NaN注入を有効にし、`n_inject`個のNaNを注入します。オッズ、関数およびライブラリのリスト、または記録/再生状態は変更しません。

```
enable_nan_injection(; odds::Int = 10, n_inject::Int = 1, functions::Array{FunctionRef} = [], libraries::Array{String} = [])
```

NaN注入を有効にします。オプションで注入のオッズ、注入するNaNの数、およびNaNを注入する関数/ライブラリを設定できます。指定されていない引数はデフォルトに上書きされます。

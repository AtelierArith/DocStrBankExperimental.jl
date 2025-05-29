```
tf_enable_nan_injection(n_inject::Int)
```

NaN注入を有効にし、`n_inject`個のNaNを注入します。オッズ、関数およびライブラリのリスト、または記録/再生状態は変更しません。

```
tf_enable_nan_injection(; odds::Int = 10, n_inject::Int = 1, functions::Array{FunctionRef} = [], libraries::Array{String} = [])
```

NaN注入を有効にします。注入のオッズや注入するNaNの数、NaNを注入する関数/ライブラリをオプションで設定できます。指定されていない引数はデフォルトに上書きされます。

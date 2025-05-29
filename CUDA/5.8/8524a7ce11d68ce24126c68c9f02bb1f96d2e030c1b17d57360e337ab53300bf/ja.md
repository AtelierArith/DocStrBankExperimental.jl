```
CuModule(data, options::Dict{CUjit_option,Any})
CuModuleFile(path, options::Dict{CUjit_option,Any})
```

データまたはデータを含むファイルからCUDAモジュールを作成します。データはPTXコード、CUBIN、またはFATBINである可能性があります。

`options`は、JITオプションとそれぞれの値のオプションの辞書です。

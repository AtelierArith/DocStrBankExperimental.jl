```
DLPack
```

`DLPack`モジュールは、JuliaとJAX、CuPy、PyTorchなどのPythonライブラリ間でテンソルオブジェクトの双方向データ交換を促進するためのJuliaインターフェースを提供します（[DLPackプロトコル][1]をサポートするすべてのPythonライブラリ）。

CPUおよびCUDA配列を共有およびラップでき、`PyCall`および`PythonCall`の両方を介したインターフェースをサポートしています。

[1]: https://data-apis.org/array-api/latest/design*topics/data*interchange.html

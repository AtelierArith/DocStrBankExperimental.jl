```
ftnsread(filename)
```

FROSTT `.tns` ファイル 'filename' の内容を Finch COO テンソルに読み込みます。

この関数を利用するには、[TensorMarket](https://github.com/willow-ahrens/TensorMarket.jl) をロードする必要があります。

!!! danger
    このファイル形式はテンソルのサイズや eltype を記録せず、アーカイブ目的のみに提供されています。


参照: [tnsread](http://willowahrens.io/TensorMarket.jl/stable/#TensorMarket.tnsread)

```
load_camb_Cℓs(;path_prefix, custom_tensor_params=nothing, 
    unlensed_scalar_postfix, unlensed_tensor_postfix, lensed_scalar_postfix, lenspotential_postfix)
```

CAMBファイルからいくつかのCℓをロードします。

`path_prefix`はファイルのプレフィックスを指定し、その後、通常のCAMBポスフィックスである`scalCls.dat`、`tensCls.dat`、`lensedCls.dat`、`lenspotentialCls.dat`を持つことが期待されます。他のキーワード引数で指定されない限り。`custom_tensor_params`は、ファイルから読み込むのではなく、`unlensed_tensors`のためにCAMBを直接呼び出すために使用できます（多くの場合、このファイルは保存されません）。値はDict/NamedTupleである必要があり、`camb`への呼び出しに渡されます。例えば、ゼロテンソルの場合は`custom_tensor_params=(r=0,)`のようになります。

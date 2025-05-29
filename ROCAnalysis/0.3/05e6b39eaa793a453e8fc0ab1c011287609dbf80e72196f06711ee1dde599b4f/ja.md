```
AUC(::roc; pfa=1.0, pmiss=1.0, normalize=true)
```

は、従来の曲線下面積（AUC）を計算し、`AUC → 1` がより良いパフォーマンスを示すことを意味します。

大まかに言えば、`AUC(args) == 1 - auc(args)` です。

オプションのパラメータ `pfa` または `pmiss` は、ROC曲線の一部のみを統合することを制限します。`normalize` は、部分ROCを自明なROCと比較することを示します。

この関数は、`AUC(targets::Vector, nontargets::Vector; kwargs...)` としても呼び出すことができます。

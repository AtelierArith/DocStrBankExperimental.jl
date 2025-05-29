```
function plot_compare_dft(tbc, bs; tbc2=missing)
```

バンド構造の比較をプロットします。これは、タイトバインディング結晶オブジェクト（`tb_crys`）と、DFTから直接得られたバンド構造（`dftout`または`bs`オブジェクトのいずれか）との比較です。

k点は`bs`オブジェクトによって固定されています。

`tbc2`はオプションの第二の`tbc_crys`です。

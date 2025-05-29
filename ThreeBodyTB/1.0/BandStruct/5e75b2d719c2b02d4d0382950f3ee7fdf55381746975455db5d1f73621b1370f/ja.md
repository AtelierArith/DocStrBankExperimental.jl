```
function plot_bandstr_dos(tbc::tb_crys)
```

対称性に基づいて導出されたkラインとDOSを一緒にプロットします。このバージョンは、以前のSCF計算からの`tb_crys`オブジェクトを受け取ります。`tbc.crys`が標準化されていない場合は、SCFを再実行する必要があります。

`plot_bandstr_sym`と`dos`を参照してください。

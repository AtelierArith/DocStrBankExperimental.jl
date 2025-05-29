```
rate(R, model::ModelDMSM, pfv::ProjectedF, pfq::ProjectedF; 
    ell_max=nothing, use_measurements=false)
```

与えられたモデル、投影された $g_\chi$ (`pfv`)、投影された $f_s^2$ (`pfq`)、およびクォータニオンまたはローターとして与えられた回転 `R` に対してレートを計算します（他の回転が必要な場合は、`Quaternionic.jl` の変換メソッドを参照してください）。 `R` はクォータニオンまたはローターのベクトルでも構いません。

使用される最大 $\ell$ は、指定された `ell_max` と `pfv` および `pfq` のそれぞれの最大 $\ell$ の最小値です。

ここでの測定値の使用は現在遅く、推奨されていません。

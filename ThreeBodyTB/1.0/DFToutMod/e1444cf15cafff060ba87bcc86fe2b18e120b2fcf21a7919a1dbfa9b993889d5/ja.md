```
function makedftout(crys::crystal, energy::Number, energy_smear::Number,  forces, stress, bandstruct=missing; prefix="PREFIX", outdir="TMPDIR", tot_charge=0.0)
```

dftoutのコンストラクタ。通常、DFT出力ファイルを読み込む関数によって呼び出され、直接呼び出されることはありません。

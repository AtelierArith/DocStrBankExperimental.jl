```
profiledensity!(f::Indexable, pr::MixedModelProfile;
                ptyp::Char='σ',
                zbd=3,
                share_y_scale=true).
```

パラメータ `ptyp` で始まるプロファイル ζ の密度プロットを `pr` から `f` へ追加します。

有効な `ptyp` 値は 'β'、'σ'、および 'θ' です。

`share_y_scale` が true の場合、各ファセットは共通の y スケールを共有します。

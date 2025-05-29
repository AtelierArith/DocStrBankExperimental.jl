```
vdi(v::VowelSpace; unstandardize=true)
```

与えられた `VowelSpace`、`v` の母音分散指数 (vdi) を計算します。実際には、母音空間密度の全変動の修正です。詳細はKelley & Aalto (2019, Measuring the dispersion of density in head and neck cancer patients' vowel spaces: The vowel dispersion index, *Canadian Acoustics 47*(3), 114-115) に記載されています。vdiは無次元数であることに注意してください。

# 引数

  * `v` vdiを計算するための `VowelSpace`
  * `unstandardize` (キーワード) `v` の半正規化されたF1およびF2をHz（または `v` が作成されたときに渡された単位）に変換するフラグ。

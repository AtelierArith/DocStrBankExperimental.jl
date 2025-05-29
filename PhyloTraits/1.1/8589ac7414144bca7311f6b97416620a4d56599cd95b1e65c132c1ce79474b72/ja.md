```
empiricalDNAfrequencies(DNAdata::AbstractDataFrame, DNAweights,
                        correction=true, useambiguous=true)
```

DNAデータ`DNAdata`の塩基頻度を推定します。順序はACGTです。

  * `DNAdata`: データフレーム。すべての列が使用されます。最初の列が種名を示す場合は、経験的頻度を計算する前に無視する方法を見つけてください。例えば、`empiricalDNAfrequencies(view(DNAdata, :, 2:size(DNAdata, 2)))`のようにします。データ型は`BioSymbols.DNA`または`Char`または`String`でなければなりません。警告: これは最初の列のみでチェックされます。
  * `DNAweights`: 各列に重みを付けるための重みのベクトルです。
  * `correction`: `true`の場合、各カウントに1を加え、分母に4を加えて、より安定した推定量を得ます。これは、1/4のベイズ事前分布と二項推定におけるAgresti-Coull区間に似ています。
  * `useambiguous`: `true`の場合、あいまいな塩基が使用されます（ギャップとNを除く）。例えば、`Y`は`C`に0.5の重みを、`T`に0.5の重みを加えます。

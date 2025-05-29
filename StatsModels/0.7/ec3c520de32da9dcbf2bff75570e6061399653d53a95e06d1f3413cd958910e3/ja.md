```
SeqDiffCoding([base[, levels]])
```

各レベルを順番にコーディングして「順次差分」仮説をテストします。これは、各レベルをその下のレベルと比較します（2番目のレベルから始まります）。具体的には、$n$番目の予測子は、レベル$n$と$n+1$の間の差がゼロであるという仮説をテストします。

差分は`levels`の順序で計算されます。`levels`が省略されるか`nothing`の場合、`ContrastsMatrix`を構築する際に`levels`関数を呼び出すことでデータから決定されます。`base`が省略されるか`nothing`の場合、最初のレベルがベースとして使用されます。

# 例

```jldoctest seqdiff
julia> seqdiff = StatsModels.ContrastsMatrix(SeqDiffCoding(), ["a", "b", "c", "d"]).matrix
4×3 Matrix{Float64}:
 -0.75  -0.5  -0.25
  0.25  -0.5  -0.25
  0.25   0.5  -0.25
  0.25   0.5   0.75
```

順次差分コーディングの解釈は、コントラスト行列自体からは見えにくいかもしれません。対応する仮説行列は、より明確な図を示します。仮説行列の行から、これらのコントラストが最初と2番目のレベル、2番目と3番目、3番目と4番目の間の差をテストしていることがわかります：

```jldoctest seqdiff
julia> StatsModels.hypothesis_matrix(seqdiff)
3×4 Matrix{Int64}:
 -1   1   0  0
  0  -1   1  0
  0   0  -1  1
```

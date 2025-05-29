```
 MSx, CI = MSEn(Sig, Mobj)
```

データ系列 `Sig` のマルチスケールエントロピー値のベクトル `MSx` と複雑性指数 `CI` を、マルチスケールオブジェクト `Mobj` によって指定されたパラメータを使用して、粗いグレイン（デフォルト）で3つの時間スケールにわたって返します。

```
 MSx, CI = MSEn(Sig::AbstractArray{T,1} where T<:Real, Mobj::NamedTuple; Scales::Int=3, 
                      Methodx::String="coarse", RadNew::Int=0, Plotx::Bool=false)
```

データ系列 `Sig` のマルチスケールエントロピー値のベクトル `MSx` と複雑性指数 `CI` を、マルチスケールオブジェクト `Mobj` によって指定されたパラメータと以下の「キーワード」引数を使用して返します。

# 引数:

`Scales`   - 時間スケールの数、整数 > 1 （デフォルト: 3）

`Method`   - グレイン方法、次のいずれか:                {`coarse`,`modified`,`imf`,`timeshift`,`generalized`} [デフォルト = `coarse`]                 これらのグレイン手順に関する詳細は、EntropyHubガイドを参照してください。

`RadNew`   - 半径再スケーリング方法、範囲 [1 4] の整数。               `Mobj` によって指定されたエントロピーが `SampEn` または `ApEn` の場合、                RadNew は各時間スケール (Xt) で半径閾値を更新できるようにします。もし `Mobj` によって指定された半径値 (`r`) がある場合、               これは再スケーリング係数となり、そうでない場合は               0.2（デフォルト）に設定されます。RadNew の値は次のいずれかの方法を指定します:

```
          [1]    標準偏差          - r*std(Xt)

          [2]    分散              - r*var(Xt) 

          [3]    平均絶対偏差     - r*mean_ad(Xt) 

          [4]    中央絶対偏差     - r*med_ad(Xt)
```

`Plotx`    - Plotx == true の場合、各時間スケールでのエントロピー値のプロットを返します               （すなわち、マルチスケールエントロピー曲線） [デフォルト: false]

`これらのグレイン手順に関する詳細は、EntropyHubガイドを参照してください。`

# 参照: `MSobject`, `rMSEn`, `cMSEn`, `hMSEn`, `SampEn`, `ApEn`, `XMSEn`

# 参考文献:

```
 [1] Madalena Costa, Ary Goldberger, and C-K. Peng,
         "複雑な生理的時系列のマルチスケールエントロピー分析."
         Physical review letters
         89.6 (2002): 068102.

 [2] Vadim V. Nikulin, and Tom Brismar,
         "「複雑な生理的時系列のマルチスケールエントロピー分析」に関するコメント." 
         Physical review letters 
         92.8 (2004): 089803.

 [3] Madalena Costa, Ary L. Goldberger, and C-K. Peng. 
         "Costa, Goldberger, and Peng の返信." 
         Physical Review Letters
         92.8 (2004): 089804.

 [4] Madalena Costa, Ary L. Goldberger and C-K. Peng,
         "生物信号のマルチスケールエントロピー分析." 
         Physical review E 
         71.2 (2005): 021906.

 [5] Ranjit A. Thuraisingham and Georg A. Gottwald,
         "生理データのマルチスケールエントロピー分析について."
         Physica A: Statistical Mechanics and its Applications
         366 (2006): 323-332.

 [6] Meng Hu and Hualou Liang,
         "多変量経験モード分解に基づく内因性モードエントロピーとその神経データ分析への応用." 
         Cognitive neurodynamics
         5.3 (2011): 277-284.

 [7] Anne Humeau-Heurtier 
         "マルチスケールエントロピーアルゴリズムとその変種: レビュー." 
         Entropy 
         17.5 (2015): 3110-3123.

 [8] Jianbo Gao, et al.,
         "生物信号のマルチスケールエントロピー分析: 基本的な二重スケーリング法則." 
         Frontiers in computational neuroscience 
         9 (2015): 64.

 [9]  Paolo Castiglioni, et al.,
         "心血管信号のマルチスケールサンプルエントロピー: スケール間の固定または変動許容の選択がその評価と解釈に影響を与えるか?. " 
         Entropy
         19.11 (2017): 590.

 [10] Tuan D Pham,
         "生理信号の時間シフトマルチスケールエントロピー分析." 
         Entropy 
         19.6 (2017): 257.

 [11] Hamed Azami and Javier Escudero,
         "単変量マルチスケールサンプルおよび分散エントロピーにおける粗いグレインアプローチ." 
         Entropy 20.2 (2018): 138.

 [12] Madalena Costa and Ary L. Goldberger,
         "一般化マルチスケールエントロピー分析: 人間の心拍時系列の複雑なボラティリティを定量化するための応用." 
         Entropy 17.3 (2015): 1197-1203.
```

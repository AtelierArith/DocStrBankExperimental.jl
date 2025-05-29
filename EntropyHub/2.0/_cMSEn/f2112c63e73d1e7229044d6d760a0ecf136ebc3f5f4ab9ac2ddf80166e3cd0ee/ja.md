```
MSx, CI = cMSEn(Sig, Mobj)
```

データシーケンス（`Sig`）に対して、マルチスケールオブジェクト（`Mobj`）によって指定されたパラメータを使用して、3つの時間スケールにわたる複合マルチスケールエントロピー法を使用して、複合マルチスケールエントロピー値のベクトル（`MSx`）を返します。

```
MSx, CI = cMSEn(Sig::AbstractArray{T,1} where T<:Real, Mobj::NamedTuple;  
                    Scales::Int=3, RadNew::Int=0, Refined::Bool=false, Plotx::Bool=false)
```

データシーケンス（`Sig`）に対して、マルチスケールオブジェクト（`Mobj`）によって指定されたパラメータと以下の「キーワード」引数を使用して、複合マルチスケールエントロピー値のベクトル（`MSx`）を返します。

# 引数:

`Scales`   - 時間スケールの数、1より大きい整数（デフォルト: 3）

`RadNew`   - 半径再スケーリング法、範囲[1 4]の整数。              `Mobj`によって指定されたエントロピーが`SampEn`または`ApEn`の場合、               RadNewは各時間スケール（Xt）で半径の閾値を更新できるようにします。              `Mobj`によって指定された半径値（`r`）がある場合、              これは再スケーリング係数となり、そうでない場合は              0.2（デフォルト）に設定されます。RadNewの値は次のいずれかの               方法を指定します：

```
         [1]    標準偏差          - r*std(Xt)

         [2]    分散              - r*var(Xt) 

         [3]    平均絶対偏差     - r*mean_ad(Xt) 

         [4]    中央絶対偏差     - r*med_ad(Xt)
```

`Refined`  - 洗練された複合MSEn法。`Refined == true`で、               `Mobj`によって指定されたエントロピー関数が`SampEn`または`FuzzEn`の場合、cMSEnは               洗練された複合マルチスケールエントロピー（rcMSEn）を返します（デフォルト: false）

`Plotx`    - `Plotx`がtrueの場合、各時間スケールでのエントロピー値のプロット（すなわち、マルチスケールエントロピー曲線）を返します（デフォルト: false）

# 参照: `MSobject`, `rMSEn`, `MSEn`, `hMSEn`, `SampEn`, `ApEn`, `XMSEn`

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
    "Costa, Goldberger, and Pengの返信." 
    Physical Review Letters
    92.8 (2004): 089804.

 [4] Shuen-De Wu, et al.,
    "複合マルチスケールエントロピーを用いた時系列分析." 
    Entropy 
    15.3 (2013): 1069-1084.

[5] Shuen-De Wu, et al.,
    "洗練された複合マルチスケールエントロピーを用いた複雑な時系列の分析." 
    Physics Letters A 
    378.20 (2014): 1369-1374.

[6] Azami, Hamed, Alberto Fernández, and Javier Escudero.
    "生物医学信号分析のための標準偏差に基づく洗練されたマルチスケールファジーエントロピー." 
    Medical & biological engineering & computing 55 (2017): 2037-2052.
```

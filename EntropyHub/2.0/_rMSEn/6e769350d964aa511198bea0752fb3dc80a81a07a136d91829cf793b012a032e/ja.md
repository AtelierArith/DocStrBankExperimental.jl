```
MSx, CI = rMSEn(Sig, Mobj)
```

データ系列（`Sig`）の洗練されたマルチスケールエントロピー値のベクトル（`MSx`）と複雑性指数（`CI`）を、マルチスケールオブジェクト（`Mobj`）によって指定されたパラメータと、以下のデフォルトパラメータを使用して返します：スケール = 3、バターワースLPFの次数 = 6、スケール（T）でのバターワースLPFのカットオフ周波数：Fc = 0.5/T。`Mobj`によって指定されたエントロピー関数がSampEnまたはApEnの場合、rMSEnは、`Mobj`によって`r`値が提供されていない場合、各スケールでデータ系列（Xt）の閾値半径を0.2std(Xt)に更新し、`r`が指定されている場合はr.std(Xt)に設定します。

```
MSx, CI = rMSEn(Sig::AbstractArray{T,1} where T<:Real, Mobj::NamedTuple; Scales::Int=3, 
                    F_Order::Int=6, F_Num::Float64=0.5, RadNew::Int=0, Plotx::Bool=false)
```

データ系列（`Sig`）の洗練されたマルチスケールエントロピー値のベクトル（`MSx`）と複雑性指数（`CI`）を、マルチスケールオブジェクト（`Mobj`）によって指定されたパラメータと、以下の「キーワード」引数を使用して返します：

# 引数：

`Scales`   - 時間スケールの数、整数 > 1（デフォルト = 3）

`F_Order`  - バターワースローパスフィルタの次数、正の整数（デフォルト：6）

`F_Num`    - バターワースローパスフィルタのカットオフ周波数の分子、スカラー値で範囲 [0 < `F_Num` < 1]。各スケール（T）でのカットオフ周波数は次のようになります：Fc = `F_Num/T`。（デフォルト：0.5）

`RadNew`   - 半径再スケーリング方法、範囲 [1 4] の整数。`Mobj`によって指定されたエントロピーが`SampEn`または`ApEn`の場合、`RadNew`は各時間スケール（Xt）で半径閾値を更新できるようにします。`Mobj`によって半径値（`r`）が指定されている場合、これは再スケーリング係数となり、そうでない場合は0.2（デフォルト）に設定されます。`RadNew`の値は次のいずれかの方法を指定します：

```
         [1]    標準偏差          - r*std(Xt)

         [2]    分散              - r*var(Xt) 

         [3]    平均絶対偏差     - r*mean_ad(Xt) 

         [4]    中央絶対偏差     - r*med_ad(Xt)
```

`Plotx`    - `Plotx` == true の場合、各時間スケールでのエントロピー値のプロット（すなわち、マルチスケールエントロピー曲線）を返します [デフォルト：false]

# 参照： `MSobject`, `MSEn`, `cMSEn`, `hMSEn`, `SampEn`, `ApEn`, `XMSEn`

# 参考文献：

```
[1] Madalena Costa, Ary Goldberger, and C-K. Peng,
    "複雑な生理学的時系列のマルチスケールエントロピー分析。"
    Physical review letters
    89.6 (2002): 068102.

[2] Vadim V. Nikulin, and Tom Brismar,
    "「複雑な生理学的時系列のマルチスケールエントロピー分析」に関するコメント。" 
    Physical review letters 
    92.8 (2004): 089803.

[3] Madalena Costa, Ary L. Goldberger, and C-K. Peng. 
    "Costa, Goldberger, and Pengの返信。" 
    Physical Review Letters
    92.8 (2004): 089804.

[4] José Fernando Valencia, et al.,
    "洗練されたマルチスケールエントロピー：健康な被験者と大動脈狭窄の被験者における心拍変動の24時間ホルター記録への応用。" 
    IEEE Transactions on Biomedical Engineering 
    56.9 (2009): 2202-2213.

[5] Puneeta Marwaha and Ramesh Kumar Sunkaria,
    "洗練されたマルチスケールエントロピーのための閾値値'r'の最適選択。" 
    Cardiovascular engineering and technology 
    6.4 (2015): 557-576.
```

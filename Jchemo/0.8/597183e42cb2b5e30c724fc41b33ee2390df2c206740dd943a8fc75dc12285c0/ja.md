```
mbplskdeda(; kwargs...)
mbplskdeda(Xbl, y; kwargs...)
mbplskdeda(Xbl, y, weights::Weight; kwargs...)
```

マルチブロック PLS-KDEDA。

  * `Xbl` : Xデータのブロックのリスト（行列のベクトル） 通常、(n, p)データからの関数`mblock`の出力。
  * `y` : 単変量クラスメンバーシップ (n)。
  * `weights` : 観測値の重み (n)。`Weight`型でなければならない（例えば、関数`mweight`を参照）。

キーワード引数：

  * `nlv` : 計算する潜在変数 (LVs = スコア) の数。
  * `bscal` : ブロックスケーリングのタイプ。可能な値については関数`blockscal`を参照。
  * `prior` : クラスメンバーシップのための事前確率のタイプ。可能な値は、`:prop`（比例）、`:unif`（一様）、または各クラスの事前重みを与えるベクトル（ベクトルの場合、`mlev(y)`と同じ順序にソートされている必要があります）。
  * 関数`dmkern`のキーワード引数（バンド幅定義）もここで指定できます。
  * `scal` : ブール値。`true`の場合、`Xbl`のブロックの各列とYdummyは、MBPLS計算においてブロックスケーリングの前にその未修正の標準偏差でスケーリングされます。

関数`mbplsqda`と同様ですが、クラス密度は`dmnorm`の代わりに`dmkern`から推定されます。

例については関数`mbplslda`を参照してください。

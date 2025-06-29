```
CycleShuffle(n::Int = 7, σ = 0.5)
```

サイクルシャッフルされたサロゲート[^Theiler1994]は、データ内の連続する局所ピークを特定し、ピーク間のサイクルをシャッフルします。[`BlockShuffle`](@ref)に似ていますが、ここでの「ブロック」は次のように定義されます。

1. 時系列はガウス関数（`DSP.gaussian(n, σ)`）との畳み込みによって平滑化されます。
2. 平滑化された信号の局所最大値がピークを定義し、それによりそれらの間のブロックが決まります。
3. 時系列の最初と最後のインデックスは決してピークにはなりえず、したがって、時系列の開始または終了に非常に近い位置にピークを持つ信号はうまく機能しない可能性があります。さらに、最初のピークの前や最後のピークの後のポイントは決してシャッフルされません。
4. 定義されたブロックは[`BlockShuffle`](@ref)のようにランダムにシャッフルされます。

CSSは、信号がサイクル間に動的相関のない周期的オシレーターによって生成されるという帰無仮説をテストするために使用されます。つまり、サイクルの進化は決定論的ではありません。

さらに[`PseudoPeriodic`](@ref)も参照してください。

[^Theiler1994]: J. Theiler, On the evidence for low-dimensional chaos in an epileptic electroencephalogram, [Phys. Lett. A 196](https://doi.org/10.1016/0375-9601(94)00856-K)

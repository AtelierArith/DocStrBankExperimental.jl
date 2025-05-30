```
WLS(shufflemethod::Surrogate = IAAFT();
    f::Union{Nothing, Function} = Statistics.cor,
    rescale::Bool = true,
    wt::Wavelets.WT.OrthoWaveletClass = Wavelets.WT.Daubechies{16}())
```

次の手順で生成されたウェーブレットサロゲート：

1. 信号のウェーブレット変換を計算します。これにより、ダイアディックスケールのセットにわたる詳細係数のセットが得られます。Keylock (2006) のように、ここでは最大重複離散ウェーブレット変換（MODWT）を使用して、各スケールでの係数の数が同じになるようにします。
2. 提供された `shufflemethod` を使用して、各ダイアディックスケールで詳細係数をシャッフルします。代替手段については、以下の「シャッフル方法」を参照してください。
3. シャッフルされた詳細係数に逆ウェーブレット変換を適用して、サロゲート時系列を取得します。

## シャッフル方法

このパッケージから任意のサロゲートを使用して、各ダイアディックスケールでの詳細係数のランダム化を行うことができます。

以下の方法が文献で議論されています（他にも存在するかもしれません）：

  * 各スケール内のウェーブレット係数のランダムな順列（Breakspear et al., 2003）。この動作を得るには、`WLS(x, RandomShuffle(), rescale = false, f = nothing)` を使用します。
  * 各スケール内のウェーブレット係数の循環的回転（Breakspear et al., 2003）。この動作を得るには、`WLS(x, Circshift(1:length(x)), rescale = false, f = nothing)` を使用します。
  * 各スケール内のウェーブレット係数のブロック再サンプリング（Breakspear et al., 2003）。この動作を得るには、`WLS(x, BlockShuffle(nblocks, randomize = true), rescale = false, f = nothing)` を使用します。
  * 各スケール内のウェーブレット係数のIAAFT再サンプリング（Keylock, 2006）。この動作を得るには、`WLS(x, IAAFT(), rescale = true, f = Statistics.cor)` を使用します。この方法は、信号の局所的な平均と分散の構造を保持しますが、信号の非線形特性（すなわち、ハースト指数）をランダム化します[^Keylock2006]。したがって、これらのサロゲートは元の信号の非線形特性の変化をテストするために使用できます。IAAFTサロゲートとは対照的に、IAAFTウェーブレットサロゲートは非定常性も保持します。他の `shufflemethod` を使用すると、必ずしも非定常性が保持されるわけではありません。非定常信号に対処するために、Keylock (2006) は高い消失モーメントを持つウェーブレットの使用を推奨しています。したがって、私たちのデフォルトは16の消失モーメントを持つダウベシーウェーブレットを使用することです。*注：ランク順序付けステップ（[^Keylock2006]のステップ[v]）の後の反復手順は、この実装では実行されません。*

デフォルトの方法とパラメータは、Keylock (2006) のIAAFTウェーブレットサロゲートの動作を再現します。

## エラー最小化

Keylock (2006) で導入された [`IAAFT`](@ref) アプローチでは、各レベルの詳細係数がエラーファンクションを最小化するために循環的に回転されます。Breakspear et al. (2003) で導入された方法は、このエラー最小化を適用しません。

私たちの実装では、`WLS` コンストラクタの `f` パラメータを使用して、このオプションをオン/オフに切り替えることができます。`f = nothing` はエラー最小化をオフにします。`f` が統計量を計算する二引数関数に設定されている場合（例えば、`f = Statistics.cor`）、各スケールの詳細係数はその関数が最大化されるまで循環的に回転されます（したがって「エラー」が最小化されます）。何らかのエラーファンクションを*最小化*したい場合は、代わりに関数の適切な変換を提供してください。例えば、二乗平均平方根偏差を使用する場合、`rmsd_inv(x, y) = 1 - StatsBase.rmsd(x, y)` と定義し、`f = rmsd_inv` に設定します。

## 再スケーリング

`rescale == true` の場合、サロゲート値は元の時系列の値にマッピングされます。これは [`AAFT`](@ref) アルゴリズムと同様です。`rescale == false` の場合、サロゲート値は元の時系列の値に制約されません。[`AAFT`](@ref) または [`IAAFT`](@ref) シャッフルが使用される場合、`rescale` は `true` に設定する必要があります。他の方法では、必ずしもそうする必要はありません。

[^Breakspear2003]: Breakspear, M., Brammer, M., & Robinson, P. A. (2003). Construction of multivariate surrogate sets from nonlinear data using the wavelet transform. Physica D: Nonlinear Phenomena, 182(1-2), 1-22.

[^Keylock2006]: C.J. Keylock (2006). "Constrained surrogate time series with preservation of the mean and variance structure". Phys. Rev. E. 73: 036707. doi:10.1103/PhysRevE.73.036707.

```

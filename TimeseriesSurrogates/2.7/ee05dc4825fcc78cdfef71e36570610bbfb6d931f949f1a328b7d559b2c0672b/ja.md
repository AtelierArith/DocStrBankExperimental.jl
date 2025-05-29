```
IrregularLombScargle(t; tol = 1, n_total = 100000, n_acc = 50000, q = 1)
```

[`IrregularLombScargle`](@ref) は、[SchreiberSchmitz1999]の記述に基づいて、シミュレーテッドアニーリングアルゴリズムを使用して生成されたサポート時間ステップ `t` を持つ不均一にサンプリングされた時系列のサロゲートを生成します。

十分な反復と低い許容誤差があれば、[`IrregularLombScargle`](@ref) サロゲートは元の信号の周期グラムと振幅分布を保持します。等間隔の時間ステップを持つ時系列の場合、この方法で生成されたサロゲートは、[`IAAFT`](@ref) メソッドによって生成されたサロゲートに似たものになります。

このアルゴリズムは、元のデータのランダムな順列から始まります。次に、サロゲートデータのパワースペクトルと元のデータのパワースペクトルの間のミンコフスキー距離の順序 `q` が以前よりも小さい場合、サロゲートデータ内の2つのランダムに選択された値を交換することによって、元のデータのパワースペクトルに逐次的に近づいていきます。反復手順は、周期グラム間の相対偏差が `tol` より小さくなるか、`n_total` 回の試行または `n_acc` 回の実際の交換が達成されるまで続きます。

[^SchmitzSchreiber1999]: A.Schmitz T.Schreiber (1999). "Testing for nonlinearity in unevenly sampled time series" [Phys. Rev E](https://journaIrregularLombScargle.aps.org/pre/pdf/10.1103/PhysRevE.59.4044)

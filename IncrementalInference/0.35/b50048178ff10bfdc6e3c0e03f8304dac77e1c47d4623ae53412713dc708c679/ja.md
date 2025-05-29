```julia
calcPerturbationFromVariable(fgc, from_var_ipc; tol)

```

入力変数からの `::Pair` のベクトルとしての infoPerCoord ベクトルのタプルを返します。すなわち、`fromVar::Int => infoPerCoord` です。例えば、バイナリの `LinearRelative` ファクターは、入力から他の1つの変数への一対一の影響を持っています。

注意

  * `fgc` の勾配が最新であると仮定します。そうでない場合は、最初に `fgc(measurement..., pts...)` を実行してください。
  * `tol` は勾配を新しい許容誤差に再計算するのではなく、`fgc` にキャッシュされた値を使用して精度を予測します。

例

```julia
# セットアップ
fct = LinearRelative(MvNormal([10;0],[1 0; 0 1]))
measurement = ([10.0;0.0],)
varTypes = (ContinuousEuclid{2}, ContinuousEuclid{2})
pts = ([0;0.0], [9.5;0])

# 勾配ファンクタオブジェクトを作成
fgc = FactorGradientsCached!(fct, varTypes, measurement, pts);
# まずキャッシュされた勾配を更新する必要があります
fgc(measurement..., pts...)

# ファクターに対する勾配を通じて摂動の影響を確認
ret = calcPerturbationFromVariable(fgc, [1=>[1;1]])

@assert isapprox(ret[2], [1;1])
```

DevNotes

  * FIXME `fromVar` を1つ以上に拡張して n-ary ソースファクターをサポートします。

関連

[`FactorGradientsCached!`](@ref), [`checkGradientsToleranceMask`](@ref)

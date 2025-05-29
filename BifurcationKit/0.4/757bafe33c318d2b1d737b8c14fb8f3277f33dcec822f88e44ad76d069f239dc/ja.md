```julia
newton(probPO, orbitguess, options; kwargs...)

```

これは、直交コレクション法を使用して周期軌道を計算するためのニュートンソルバーです。線形ソルバーは`options`で適切に設定する必要があることに注意してください。

# 引数

[`newton`](@ref)と似ていますが、`prob`は[`PeriodicOrbitOCollProblem`](@ref)の型です。

  * `prob` 射撃関数Gをエンコードする`<: PeriodicOrbitOCollProblem`型の問題。
  * `orbitguess` 周期軌道の推測。
  * `options` 通常の[`newton`](@ref)メソッドと同じ。

# オプション引数

  * `jacobian` 線形アルゴリズムの選択を指定します。これは`(AutoDiffDense(), )`に属する必要があります。これは、ヤコビアンdGを反転する方法を選択するために使用されます。

      * `AutoDiffDense()`の場合。ヤコビアンは密な行列として形成されます。直接ソルバーまたは`options`を使用した反復ソルバーを使用できます。ヤコビアンはインプレースで形成されます。
      * `DenseAnalytical()`の場合。`AutoDiffDense`と同様ですが、ヤコビアンはADと解析式の混合を使用して形成されます。

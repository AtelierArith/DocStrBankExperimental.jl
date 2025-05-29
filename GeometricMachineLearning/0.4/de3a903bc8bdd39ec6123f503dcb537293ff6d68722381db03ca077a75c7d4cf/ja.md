`NeuralNetworkIntegrator` は、[`SympNet`](@ref) や [`ResNet`](@ref) などのさまざまなニューラルネットワークアーキテクチャのスーパークラスです。

このようなニューラルネットワークの目的は、常微分方程式 (ODE) の流れを近似することです。

`NeuralNetworkIntegrator` は、従来の一歩法をニューラルネットワークでモデル化していると見なすことができ、すなわち、固定された時間ステップに対して次のように実行します：

$$
    \mathtt{NeuralNetworkIntegrator}: z^{(t)} \mapsto z^{(t+1)},
$$

いくつかの ODE の流れを近似しようとします：

$$
    || \mathtt{Integrator}(z^{(t)}) - \varphi^h(z^{(t)}) || \approx \mathcal{O}(h),
$$

ここで、$\varphi^h$ は時間ステップ $h$ に対する ODE の流れマップです。

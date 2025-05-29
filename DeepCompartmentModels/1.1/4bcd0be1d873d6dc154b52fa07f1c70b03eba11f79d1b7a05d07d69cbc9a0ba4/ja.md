```
DeepCompartmentModel{T,D,M,S}
```

モデルアーキテクチャは元々[janssen2022]で説明されています。元々は、共変量と微分方程式のシステムのパラメータとの関係を学習するためにニューラルネットワークを使用し、例えばコンパートメントモデルを表します。

# 引数

  * `problem::AbstractDEProblem`: 動的システムを記述するDE問題。
  * `model`: DEパラメータの予測に使用するモデル。このパッケージはLux.jlに基づくニューラルネットワークの使用に焦点を当てています。
  * `T::Type`: パラメータと予測のデータ型。
  * `dv_compartment::Int`: 従属変数の予測のためのコンパートメントのインデックス。デフォルト = 1。
  * `sensealg`: DESolutionに対するパラメータの勾配の計算に使用する感度アルゴリズム。

[janssen2022] Janssen, Alexander, et al. "Deep compartment models: a deep learning approach for the reliable prediction of time‐series data in pharmacokinetic modeling." CPT: Pharmacometrics & Systems Pharmacology 11.7 (2022): 934-945.

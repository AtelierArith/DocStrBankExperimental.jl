```
DeepCompartmentModel(ode_fn, model, error, T=Float32; kwargs...)
```

内部的に渡されたode*fnに基づいてODEProblemを作成する便利なコンストラクタ。ode*fnに存在する偏微分方程式の数を推定しようとします。

# 引数

  * `ode_fn::Function`: 動的システムを記述する関数。
  * `model`: DEパラメータの予測に使用するモデル。このパッケージはLux.jlに基づくニューラルネットワークの使用に焦点を当てています。
  * `error::AbstractErrorModel`: 使用するエラーモデル。 [ImplicitError, AdditiveError, ProportionalError, CombinedError, CustomError] のいずれかである必要があります。
  * `T::Type`: パラメータと予測のデータ型。

# キーワード引数

  * `dv_compartment::Int`: 従属変数の予測のためのコンパートメントのインデックス。デフォルト = 1。
  * `sensealg`: DESolutionに対するパラメータの勾配の計算に使用する感度アルゴリズム。

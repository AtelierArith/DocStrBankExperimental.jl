DeepCompartmentModel(ode*fn, num*partials, model, error, T=Float32; kwargs...)

内部で渡されたode_fnに基づいてODEProblemを作成する便利なコンストラクタです。

# 引数

  * `ode_fn::Function`: 動的システムを記述する関数。
  * `num_partials::Int`: ode_fnに存在する偏微分方程式の数。
  * `model`: DEパラメータの予測に使用するモデル。このパッケージはLux.jlに基づくニューラルネットワークの使用に焦点を当てています。
  * `error::AbstractErrorModel`: 使用するエラーモデル。 [ImplicitError, AdditiveError, ProportionalError, CombinedError, CustomError] のいずれかである必要があります。
  * `T::Type`: パラメータと予測のデータ型。

# キーワード引数

  * `dv_compartment::Int`: 従属変数の予測のためのコンパートメントのインデックス。デフォルト = 1。
  * `sensealg`: DESolutionに対するパラメータの勾配の計算に使用する感度アルゴリズム。

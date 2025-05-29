qqmap(obs::ClimGrid, ref::ClimGrid, fut::ClimGrid; method="Additive", detrend=true, window::Int=15, rankn::Int=50, thresnan::Float64=0.1, keep_original::Bool=false, interp::Function = Linear(), extrap::Function = Flat())

分位数-分位数マッピングバイアス補正。

年の各ジュリアンデー（+/- **window** サイズ）について、経験的な分位数-分位数マッピングを通じて転送関数が推定されます。**ref** と **obs** の間の分位数-分位数転送関数は、ジュリアンデー（およびグリッドポイント）ベースで推定され、ジュリアンデーの周りの移動ウィンドウを使用します。したがって、特定のジュリアンデーに対して、転送関数は特定のジュリアンデーの **fut** データセットに適用されます。

**オプション**

**method::String = "Additive" (デフォルト) または "Multiplicative"**。Additiveはほとんどの気候変数に使用されます。Multiplicativeは通常、降水量や湿度などの制約のある変数です。

**detrend::Bool = true (デフォルト)**。4次の多項式が時系列に調整され、残差は分位数-分位数マッピングで補正されます。

**window::Int = 15 (デフォルト)**。特定のジュリアンデーの周りの統計的特性を抽出するために使用されるウィンドウのサイズ。

**rankn::Int = 50 (デフォルト)**。分位数推定に使用されるビンの数。デフォルトでは、0.01から0.99の間に50のビンが使用されます。ビン間の挙動はinterpキーワード引数によって制御されます。0.01および0.99の範囲外での分位数-分位数推定の挙動はextrapキーワード引数によって制御されます。

**thresnan::Float64 = 0.1 (デフォルト)**。特定のジュリアンデーの分位数-分位数マッピングの推定に許可される欠損値の割合。**treshnan**を超える欠損値がある場合、この特定のジュリアンデーの出力はNaNを返します。

**keep_original::Bool = false (デフォルト)**。**keep_original**がtrueに設定されている場合、NaNが多すぎる場合に元の値に設定されます。

**interp = Interpolations.Linear() (デフォルト)**。補正されるデータが2つの分位数ビンの間にある場合、転送関数の値は2つの最も近い分位数推定の間で線形補間されます。この引数はInterpolations.jlパッケージからのものです。

**extrap = Interpolations.Flat() (デフォルト)**。0.01-0.99の範囲外での分位数-分位数転送関数の挙動。Flat()に設定すると、バイアス補正における「インフレーション問題」が発生しないことが保証されます。この引数はInterpolation.jlパッケージからのものです。

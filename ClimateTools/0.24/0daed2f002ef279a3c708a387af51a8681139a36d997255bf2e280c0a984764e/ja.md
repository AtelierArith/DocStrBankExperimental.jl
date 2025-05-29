```
biascorrect_extremes(obs::ClimGrid, ref::ClimGrid, fut::ClimGrid; detrend=false, window::Int=15, rankn::Int=50, thresnan::Float64=0.1, keep_original::Bool=false, interp=Linear(), extrap=Flat(), gev_params::DataFrame, frac=0.25, power=1.0)
```

経験的な分位数-分位数マッピング（[`qqmap`](@ref)を参照）と一般化パレート分布のバイアス補正手法を組み合わせます。

分布の尾部は、gevparams DataFrameに含まれるパラメトリックGPDを使用して補正されます。DataFrame gevparamsには、GEVパラメータとパラメータの空間的位置を表す列:lat, :lon, :mu, :sigma, :xiがあります。各グリッドポイントについて、関数は最も近いGEVパラメータを抽出します。

**GPDに特有のオプション**

**gevparams::DataFrame**は、各グリッドポイントを補正するための（外部の）GEVパラメータを表します。

**frac=0.25**は、QQMとGPDの間でカットオフが発生する割合であり、**(maximum(x) - minimum(x))*frac**によって定義されます（例：最大値150mm、最小値30mmの場合、線形遷移は30mmから60mmの間になります）。

**power=1.0**は、遷移の形状です。

**QQMに特有のオプション**

**detrend::Bool = false (デフォルト)**。4次の多項式が時系列に調整され、残差が補正されます。

**window::Int = 15 (デフォルト)**。特定のユリウス日周辺の統計的特性を抽出するために使用されるウィンドウのサイズです。

**rankn::Int = 50 (デフォルト)**。分位数推定に使用されるビンの数です。分位数はデフォルトで0.01から0.99の間に50ビンを使用します。ビン間の挙動はinterpキーワード引数によって制御されます。0.01および0.99の範囲外での分位数-分位数推定の挙動はextrapキーワード引数によって制御されます。

**thresnan::Float64 = 0.1 (デフォルト)**。特定のユリウス日の分位数-分位数マッピングの推定に許可される欠損値の割合です。**treshnan**を超える欠損値がある場合、この特定のユリウス日の出力はNaNを返します。

**keep_original::Bool = false (デフォルト)**。**keep_original**がtrueに設定されている場合、あまりにも多くのNaNが存在する場合に元の値が設定されます。

**interp = Interpolations.Linear() (デフォルト)**。補正されるデータが2つの分位数ビンの間にある場合、転送関数の値は2つの最も近い分位数推定の間で線形補間されます。この引数はInterpolations.jlパッケージからのものです。

**extrap = Interpolations.Flat() (デフォルト)**。0.01-0.99の範囲外での分位数-分位数転送関数の挙動。Flat()に設定すると、バイアス補正における「インフレ問題」が発生しないことが保証されます。この引数はInterpolation.jlパッケージからのものです。

参照：[`qqmap`](@ref) ```

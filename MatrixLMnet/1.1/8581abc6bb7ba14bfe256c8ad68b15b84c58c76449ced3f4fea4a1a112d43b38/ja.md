```
mlmnet_bic(data::RawData, 
               lambdas::AbstractArray{Float64,1},
               alphas::AbstractArray{Float64,1}; 
               method::String="ista", isNaive::Bool=false,
               addXIntercept::Bool=true, addZIntercept::Bool=true, 
               toXReg::BitArray{1}=trues(size(get_X(data), 2)), 
               toZReg::BitArray{1}=trues(size(get_Z(data), 2)), 
               toXInterceptReg::Bool=false, toZInterceptReg::Bool=false, 
               toNormalize::Bool=true, isVerbose::Bool=true, 
               stepsize::Float64=0.01, setStepsize::Bool=true, 
               dig::Int64=12, funArgs...)
```

`mlmnet`のBIC検証を実行します。

# 引数

  * data = RawDataオブジェクト
  * lambdas = 降順に並んだ合計ペナルティからなる1次元の浮動小数点数の配列。降順でない場合はソートされます。
  * alphas = L1とL2のペナルティの混合を決定するペナルティ比からなる1次元の浮動小数点数の配列

# キーワード引数

  * methods = Elastic-netペナルティ推定法を適用する関数名; デフォルトは`ista`で、他のメソッドは`fista`、`fista_bt`、`admm`、`cd`です。
  * isNaive = ナイーブまたは非ナイーブElastic-net問題を解くかどうかを示すブールフラグ
  * addXIntercept = `X`切片（行の主効果）を含めるかどうかを示すブールフラグ。デフォルトは`true`。
  * addZIntercept = `Z`切片（列の主効果）を含めるかどうかを示すブールフラグ。デフォルトは`true`。
  * toXReg = 各`X`（行）効果を正則化するかどうかを示すビットフラグの1次元配列。デフォルトは`true`の2次元配列で、長さは`X`効果の数（`data.p`に相当）です。
  * toZReg = 各`Z`（列）効果を正則化するかどうかを示すビットフラグの1次元配列。デフォルトは`true`の2次元配列で、長さは`Z`効果の数（`data.q`に相当）です。
  * toXInterceptReg = `X`切片を正則化するかどうかを示すブールフラグ。デフォルトは`false`。
  * toZInterceptReg = `Z`切片を正則化するかどうかを示すブールフラグ。デフォルトは`false`。
  * toNormalize = `X`と`Z`の列を標準化するかどうかを示すブールフラグ（平均0、標準偏差1に）。デフォルトは`true`。
  * isVerbose = メッセージを印刷するかどうかを示すブールフラグ。デフォルトは`true`。
  * stepsize = 浮動小数点数; 更新のためのステップサイズ（座標降下法や`ista!`および`fista!`の`setStepsize`が`true`に設定されている場合は無関係）。デフォルトは`0.01`。
  * setStepsize = 固定ステップサイズを計算するかどうかを示すブールフラグ（`ista!`および`fista!`用）。デフォルトは`true`。
  * dig = 整数; ゼロ係数の精度の桁数。デフォルトは12。
  * funArgs = `fun`に渡される可変キーワード引数

# 値

Mlmnet_bicオブジェクト。

# 一部の注意事項

これはすべての他のバリアントが呼び出す基本的な`mlmnet_bic`関数です。 ```

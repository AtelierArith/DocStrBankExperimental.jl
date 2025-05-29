```
mlmnet_cvmlmnet_cv(data::RawData, 
               lambdas::AbstractArray{Float64,1},
               alphas::AbstractArray{Float64,1}, 
               rowFolds::Array{Array{Int64,1},1}, 
               colFolds::Array{Array{Int64,1},1}; 
               method::String="ista", isNaive::Bool=false,
               addXIntercept::Bool=true, addZIntercept::Bool=true, 
               toXReg::BitArray{1}=trues(size(get_X(data), 2)), 
               toZReg::BitArray{1}=trues(size(get_Z(data), 2)), 
               toXInterceptReg::Bool=false, toZInterceptReg::Bool=false, 
               toNormalize::Bool=true, isVerbose::Bool=true, 
               stepsize::Float64=0.01, setStepsize::Bool=true, 
               dig::Int64=12, funArgs...)
```

ユーザー入力からの行と列のフォールドを使用して、`mlmnet`のクロスバリデーションを実行します。

# 引数

  * data = RawDataオブジェクト
  * lambdas = 降順に並んだ合計ペナルティからなる1次元の浮動小数点数配列。降順でない場合は、ソートされます。
  * alphas = L1とL2のペナルティの混合を決定するペナルティ比からなる1次元の浮動小数点数配列
  * rowFolds = 各フォールドのインデックスを含む配列の1次元配列（各フォールドごとに1つの配列）；colFoldsと同じ長さでなければなりません。`make_folds`を呼び出すことで生成できます。これはMLBaseパッケージの`Kfold`に基づいています。
  * colFolds = 各フォールドのインデックスを含む配列の1次元配列（各フォールドごとに1つの配列）；rowFoldsと同じ長さでなければなりません。`make_folds`を呼び出すことで生成できます。これはMLBaseパッケージの`Kfold`に基づいています。

# キーワード引数

  * methods = Elastic-netペナルティ推定法を適用する関数名；デフォルトは`ista`で、他のメソッドは`fista`、`fista_bt`、`admm`、`cd`です。
  * isNaive = ナイーブまたは非ナイーブElastic-net問題を解決するかどうかを示すブールフラグ
  * addXIntercept = `X`切片（行の主効果）を含めるかどうかを示すブールフラグ。デフォルトは`true`です。
  * addZIntercept = `Z`切片（列の主効果）を含めるかどうかを示すブールフラグ。デフォルトは`true`です。
  * toXReg = 各`X`（行）効果を正則化するかどうかを示すビットフラグの1次元配列。デフォルトは`data.p`に等しい長さの`true`の2次元配列です。
  * toZReg = 各`Z`（列）効果を正則化するかどうかを示すビットフラグの1次元配列。デフォルトは`data.q`に等しい長さの`true`の2次元配列です。
  * toXInterceptReg = `X`切片を正則化するかどうかを示すブールフラグ。デフォルトは`false`です。
  * toZInterceptReg = `Z`切片を正則化するかどうかを示すブールフラグ。デフォルトは`false`です。
  * toNormalize = `X`と`Z`の列を標準化するかどうかを示すブールフラグ（平均0、標準偏差1）。デフォルトは`true`です。
  * isVerbose = メッセージを印刷するかどうかを示すブールフラグ。デフォルトは`true`です。
  * stepsize = 浮動小数点数；更新のためのステップサイズ（座標降下法や`ista!`および`fista!`の`setStepsize`が`true`に設定されている場合には無関係）。デフォルトは`0.01`です。
  * setStepsize = 固定ステップサイズを計算するかどうかを示すブールフラグ（`ista!`および`fista!`用）。デフォルトは`true`です。
  * dig = 整数；ゼロ係数の精度の桁数。デフォルトは12です。
  * funArgs = `fun`に渡される可変キーワード引数

# 値

Mlmnet_cvオブジェクト。

# 一部の注意事項

これは、すべての他のバリアントが呼び出す基本的な`mlmnet_cv`関数です。フォールドは可能な限り並行して計算されます。

```
mlmnet_perms(data::RawData, 
                  lambdas::AbstractArray{Float64,1}, alphas::AbstractArray{Float64,1};
                  method::String = "ista", isNaive::Bool=false, 
                  permFun::Function=shuffle_rows, 
                  addXIntercept::Bool=true, addZIntercept::Bool=true, 
                  toXReg::BitArray{1}=trues(data.p), 
                  toZReg::BitArray{1}=trues(data.q), 
                  toXInterceptReg::Bool=false, 
                  toZInterceptReg::Bool=false, 
                  toNormalize::Bool=true, isVerbose::Bool=true, 
                  stepsize::Float64=0.01, setStepsize=true, funArgs...)
```

RawDataオブジェクト内の応答行列Yを置換し、その後mlmnetコア関数を呼び出します。

# 引数

  * data = RawDataオブジェクト
  * lambdas = 降順に並んだ合計ペナルティからなる1次元の浮動小数点数の配列。降順でない場合はソートされます。
  * alphas = L1とL2のペナルティの混合を決定するペナルティ比からなる1次元の浮動小数点数の配列

# キーワード引数

  * methods = Elastic-netペナルティ推定法を適用する関数名; デフォルトは`ista`で、他のメソッドは`fista`、`fista_bt`、`admm`、`cd`です。
  * isNaive = ナイーブまたは非ナイーブElastic-net問題を解くかどうかを示すブールフラグ
  * permFun = `Y`を置換するために使用される関数。デフォルトは`shuffle_rows`（`Y`の行をシャッフルします）。
  * addXIntercept = `X`切片（行の主効果）を含めるかどうかを示すブールフラグ。デフォルトは`true`。
  * addZIntercept = `Z`切片（列の主効果）を含めるかどうかを示すブールフラグ。デフォルトは`true`。
  * toXReg = 各`X`（行）効果を正則化するかどうかを示すビットフラグの1次元配列。デフォルトは`true`の2次元配列で、長さは`X`効果の数（`data.p`に相当）です。
  * toZReg = 各`Z`（列）効果を正則化するかどうかを示すビットフラグの1次元配列。デフォルトは`true`の2次元配列で、長さは`Z`効果の数（`data.q`に相当）です。
  * toXInterceptReg = `X`切片を正則化するかどうかを示すブールフラグ。デフォルトは`false`。
  * toZInterceptReg = `Z`切片を正則化するかどうかを示すブールフラグ。デフォルトは`false`。
  * toNormalize = `X`と`Z`の列を標準化するかどうかを示すブールフラグ（平均0、標準偏差1に）。デフォルトは`true`。
  * isVerbose = メッセージを表示するかどうかを示すブールフラグ。デフォルトは`true`。
  * setStepsize = 固定ステップサイズを計算するかどうかを示すブールフラグ（`ista!`および`fista!`用）。デフォルトは`true`。
  * stepsize = 浮動小数点数; 更新のためのステップサイズ（座標降下法および`ista!`および`fista!`の`setStepsize`が`true`に設定されている場合は無関係）。デフォルトは`0.01`。
  * funArgs = `fun`に渡される可変キーワード引数

# 値

MLMnetオブジェクト

# 一部の注意事項

`fista!`または`ista!`のための固定ステップサイズを選択するためのデフォルトの方法は、`X*transpose(X)`および`Z*transpose(Z)`の最大固有値の積の逆数を使用することです。これは、`fista!`または`ista!`が`fun`引数に渡され、`setStepsize`が`true`に設定されているときに計算されます。`setStepsize`が`false`に設定されている場合、`stepsize`引数の値が固定ステップサイズとして使用されます。`X`および/または`Z`が非常に大きい場合、固有値を取得することは計算上の制限を超える可能性があることに注意してください。

`fista_bt!`が`fun`引数に渡されるときに、良い開始ステップサイズ（`stepsize`）と乗数（`gamma`）を指定することは難しい場合があります。ステップサイズを徐々に縮小しすぎると収束が遅くなる可能性があります。あまりにも早く行うと基準が発散する可能性があります。実際には、`stepsize`を0.01に設定することがよく機能することがわかっています; `gamma`の選択はあまり重要ではないようです。

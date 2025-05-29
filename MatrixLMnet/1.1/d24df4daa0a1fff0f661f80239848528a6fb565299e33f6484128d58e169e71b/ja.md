```
mlmnet(data::RawData, 
            lambdas::AbstractArray{Float64,1}, alphas::AbstractArray{Float64,1};
            method::String = "ista", 
            isNaive::Bool=false,
            addXIntercept::Bool=true, addZIntercept::Bool=true, 
            toXReg::BitArray{1}=trues(data.p), 
            toZReg::BitArray{1}=trues(data.q),     
            toXInterceptReg::Bool=false, toZInterceptReg::Bool=false, 
            toNormalize::Bool=true, isVerbose::Bool=true, 
            stepsize::Float64=0.01, setStepsize::Bool=true, 
            funArgs...)
```

XおよびZ予測行列を中心化および正規化し、固定ステップサイズを計算し、提供されたメソッドを使用してL1およびL2のための2つの降下リストのラムダとアルファに対して$ウォームスタート$を実行し、ユーザー入力によって必要とされる場合に結果の係数を逆変換します。

# 引数

  * data = RawDataオブジェクト
  * lambdas = 降順に並んだ合計ペナルティからなる1次元の浮動小数点配列。降順でない場合はソートされます。
  * alphas = L1とL2のペナルティの混合を決定するペナルティ比からなる1次元の浮動小数点配列

# キーワード引数

  * methods = Elastic-netペナルティ推定メソッドを適用する関数名; デフォルトは`ista`で、他のメソッドは`fista`、`fista_bt`、`admm`および`cd`です。
  * isNaive = ナイーブまたは非ナイーブElastic-net問題を解くかどうかを示すブールフラグ
  * addXIntercept = `X`切片（行の主効果）を含めるかどうかを示すブールフラグ。デフォルトは`true`です。
  * addZIntercept = `Z`切片（列の主効果）を含めるかどうかを示すブールフラグ。デフォルトは`true`です。
  * toXReg = 各`X`（行）効果を正則化するかどうかを示すビットフラグの1次元配列。デフォルトは`true`の2次元配列で、長さは`X`効果の数（`data.p`に相当）です。
  * toZReg = 各`Z`（列）効果を正則化するかどうかを示すビットフラグの1次元配列。デフォルトは`true`の2次元配列で、長さは`Z`効果の数（`data.q`に相当）です。
  * toXInterceptReg = `X`切片を正則化するかどうかを示すブールフラグ。デフォルトは`false`です。
  * toZInterceptReg = `Z`切片を正則化するかどうかを示すブールフラグ。デフォルトは`false`です。
  * toNormalize = `X`および`Z`の列を標準化（平均0、標準偏差1）するかどうかを示すブールフラグ。デフォルトは`true`です。
  * isVerbose = メッセージを印刷するかどうかを示すブールフラグ。デフォルトは`true`です。
  * stepsize = 浮動小数点; 更新のためのステップサイズ（座標降下法および`ista!`および`fista!`の`setStepsize`が`true`に設定されている場合には無関係）。デフォルトは`0.01`です。
  * setStepsize = 固定ステップサイズを計算するかどうかを示すブールフラグ（`ista!`および`fista!`用）。デフォルトは`true`です。
  * funArgs = `fun`に渡される可変キーワード引数

# 値

Mlmnetオブジェクト

# 一部の注意事項

`fista!`または`istaNet!`のための固定ステップサイズを選択するためのデフォルトメソッドは、`X*transpose(X)`および`Z*transpose(Z)`の最大固有値の積の逆数を使用することです。これは、`fista!`または`ista!`が`fun`引数に渡され、`setStepsize`が`true`に設定されているときに計算されます。`setStepsize`が`false`に設定されている場合、`stepsize`引数の値が固定ステップサイズとして使用されます。`X`および/または`Z`が非常に大きい場合、固有値を取得することは計算上の制限を超える可能性があることに注意してください。

`fista_bt!`が`fun`引数に渡されるときに、良い開始ステップサイズ（`stepsize`）と乗数（`gamma`）を指定することは難しい場合があります。ステップサイズをあまりにも徐々に縮小すると、収束が遅くなる可能性があります。あまりにも急速に行うと、基準が発散する可能性があります。実際には、`stepsize`を0.01に設定することがよく機能することがわかっています; `gamma`の選択はあまり重要ではないようです。

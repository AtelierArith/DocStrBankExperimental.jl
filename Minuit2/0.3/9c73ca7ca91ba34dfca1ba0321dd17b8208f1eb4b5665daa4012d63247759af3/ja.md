```
FCN(fnc, grad=nothing, arraycall=false, errordef=1.0)
```

Julia関数`fnc`とその勾配`grad`からJuliaFcnオブジェクトを作成します。

## 引数

  * `fnc::Function` : 最小化するJulia関数。離散引数のセットを受け入れるか、`AbstractVector`型の単一引数を受け入れることができます。これは引数`arraycall`と共に決定されます。
  * `grad::Function=nothing`; 勾配のJulia関数。入力引数は`fcn`と同じで、パラメータの数と同じ長さの`Vector`を返し、勾配を含みます。
  * `arraycall::Bool=false` : `true`の場合、関数`fcn`は`AbstractVector`型の単一引数を受け入れます。`false`の場合、関数は離散引数のセットを受け入れます。
  * `errordef::Real=1.0` : 関数の誤差定義。Minuitは、関数値を`errordef`だけ変えるために必要なパラメータ値の変化をパラメータ誤差として定義します。通常、カイ二乗フィットの場合は1、負の対数尤度の場合は0.5です。

## 戻り値

  * `JuliaFcn` : Minuitで使用できる抽象C++クラス`Minuit::FCNBase`から継承されたJuliaFcnオブジェクト。

## 使用法

```julia
fcn(x, y) = (x - 2)^2 + (y - 3)^2
grad(x, y) = [2*(x - 2), 2*(y - 3)]
jf = FCN(fcn, grad)

jf(1.0, 1.0)  # 5.0を返します
jf.grad(1.0, 1.0)  # [-2.0, -4.0]を返します

jf.nfcn # 関数呼び出しの回数を返します
jf.ngrad # 勾配呼び出しの回数を返します

jf.has_gradient # trueを返します
```

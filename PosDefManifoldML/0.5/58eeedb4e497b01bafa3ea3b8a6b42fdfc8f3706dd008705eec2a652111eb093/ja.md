```julia
function gen2ClassData(n        ::  Int,
                       k1train  ::  Int,
                       k2train  ::  Int,
                       k1test   ::  Int,
                       k2test   ::  Int,
                       separation :: Real = 0.1)
```

2つのクラス（1と2）のために、`k1train`+`k2train`を保持するランダムな*トレーニングセット*と、`k1test`+`k2test`を保持するランダムな*テストセット*を生成します。すべての行列は*n*x*n*のサイズです。

トレーニングセットとテストセットは、任意の[MLmodel](@ref)をトレーニングおよびテストするために使用できます。

`separation`は、2つのクラスがどれだけ分離可能であるかを決定する係数です。値が高いほど、2つのクラスはより分離可能です。これは$[0, 1]$の範囲内でなければならず、通常0.5の値はすでに完全な分離を決定します。

次の4つのタプルを返します。

  * トレーニングセットの`k1train`+`k2train`行列を保持する[ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1)、
  * テストセットの`k1test`+`k2test`行列を保持するℍVector、
  * トレーニングセットの行列に対応する`k1train`+`k2train`ラベル（整数）を保持するベクトル、
  * テストセットの行列に対応する`k1test`+`k2test`ラベルを保持するベクトル（クラス1には*1*、クラス2には*2*）。

**例**

```julia
using PosDefManifoldML

PTr, PTe, yTr, yTe=gen2ClassData(10, 30, 40, 60, 80, 0.25)

# PTr=トレーニングセット: クラス1のための30行列とクラス2のための40行列
# PTe=テストセット: クラス1のための60行列とクラス2のための80行列
# すべての行列は10x10
# yTr=トレーニングセットのための70ラベルのベクトル
# yTe=テストセットのための140ラベルのベクトル

```

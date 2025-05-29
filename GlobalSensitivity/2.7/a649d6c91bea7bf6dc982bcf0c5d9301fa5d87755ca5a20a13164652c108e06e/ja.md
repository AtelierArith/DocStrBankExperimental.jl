```
FractionalFactorial()
```

`FractionalFactorial` にはキーワード引数がありません。

## メソッドの詳細

Fractional Factorial メソッドは、ハダマード行列を利用して設計行列を作成し、それを使用して入力モデルのシミュレーションを実行します。主効果は、パラメータのコントラストとシミュレーション結果のベクトルとの間のドット積によって評価されます。対応する主効果と分散、すなわち主効果の二乗が、Fractional Factorial メソッドの結果として返されます。

## API

```
gsa(f, method::FractionalFactorial; num_params, p_range = nothing, kwargs...)
```

### 例

```julia
using GlobalSensitivity, Test

f = X -> X[1] + 2 * X[2] + 3 * X[3] + 4 * X[7] * X[12]
res1 = gsa(f,FractionalFactorial(),num_params = 12,samples=10)
```

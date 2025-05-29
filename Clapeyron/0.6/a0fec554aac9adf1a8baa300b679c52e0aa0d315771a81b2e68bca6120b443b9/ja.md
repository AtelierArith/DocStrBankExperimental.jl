```
EoSVirial2 <: SecondVirialModel
EoSVirial2(model;idealmodel = idealmodel(model))
```

## 入力モデル

  * `model`: 第二ビリアル係数を提供するモデル
  * `idealmodel`: 理想モデル

## 説明

基礎モデルの第二ビリアル係数を呼び出すだけのビリアルモデルです。

```
B(T,z) = B(model,T,z)
```

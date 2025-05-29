```
SingleFluidIdeal(components;
    userlocations = String[],
    Rgas = nothing,
    verbose = false,
    coolprop_userlocations = true)
```

## 入力パラメータ

  * JSONデータ（CoolPropおよびteqp形式）

## 入力モデル

  * `ancillaries`: 飽和計算の初期推定値を提供するモデル。`nothing`の場合、入力JSONから解析されます。

## 説明

単一成分の経験的EoSモデルの理想部分をインスタンス化します。`Rgas`は、物性計算中に使用される気体定数の値を設定するために使用できます。

`coolprop_userlocations`がtrueの場合、Clapeyronは流体がCoolPropライブラリに存在するかどうかを確認しようとします。

プロパティと理想項には、それぞれ`properties`および`ideal`フィールドを介してアクセスできます：

```julia-repl
julia> model = SingleFluidIdeal("water")
水の理想多パラメータ状態方程式:
 主項: -8.3204464837497 + 6.6832105275932*τ + 3.00632*log(τ)
 プランク-アインシュタイン項: 5

julia> model.ideal
理想多パラメータ係数:
 主項: -8.3204464837497 + 6.6832105275932*τ + 3.00632*log(τ)
 プランク-アインシュタイン項: 5
```

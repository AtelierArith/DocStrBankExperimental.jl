```
SingleFluid(components;
        userlocations = String[],
        ancillaries = nothing,
        ancillaries_userlocations = String[],
        estimate_pure = false,
        coolprop_userlocations = true,
        Rgas = nothing,
        verbose = false)
```

## 入力パラメータ

  * JSONデータ（CoolPropおよびteqp形式）

## 入力モデル

  * `ancillaries`: 飽和計算の初期推定値を提供するモデル。`nothing`の場合、入力JSONから解析されます。

## 説明

単一成分の経験的EoSモデルをインスタンス化します。`Rgas`は、物性計算中に使用される気体定数の値を設定するために使用できます。

`coolprop_userlocations`がtrueの場合、Clapeyronは流体がCoolPropライブラリに存在するかどうかを確認しようとします。

物性、理想項および残差項は、それぞれ`properties`、`ideal`および`residual`フィールドを介してアクセスできます：

```julia-repl
julia> model = SingleFluid("water")
水のための多パラメータ状態方程式:
 多項式のべき項: 7
 指数項: 44
 ガウス型ベル状項: 3
 非解析項: 2

julia> model.ideal
理想的な多パラメータ係数:
 主項: -8.3204464837497 + 6.6832105275932*τ + 3.00632*log(τ)
 プランク-アインシュタイン項: 5

julia> model.residual
残差多パラメータ係数:
 多項式のべき項: 7
 指数項: 44
 ガウス型ベル状項: 3
 非解析項: 2
```

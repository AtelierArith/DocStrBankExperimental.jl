```
EmpiricIdeal(components;
pure_userlocations = String[],
estimate_pure = false,
coolprop_userlocations = true,
Rgas = R̄,
verbose = false)
```

## 入力パラメータ

  * JSONデータ（CoolPropおよびteqp形式）

## 説明

多成分Empiric EoSモデルの理想部分をインスタンス化します。`Rgas`は、物性計算中に使用される気体定数の値を設定するために使用できます。

`coolprop_userlocations`がtrueの場合、Clapeyronは流体がCoolPropライブラリに存在するかどうかを確認しようとします。

`estimate_pure`がtrueの場合、JSONが見つからない場合、純粋モデルが`XiangDeiters`モデルを使用して推定されます。

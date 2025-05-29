```
MultiFluid(components;
    idealmodel = nothing,
    ideal_userlocations = String[],
    pure_userlocations = String[],
    mixing = AsymmetricMixing,
    departure = EmpiricDeparture,
    mixing_userlocations = String[],
    departure_userlocations = String[],
    estimate_pure = false,
    estimate_mixing = :off,
    coolprop_userlocations = true,
    Rgas = nothing,
    reference_state = nothing,
     verbose = false)
```

## 入力パラメータ

  * JSONデータ（CoolPropおよびteqp形式）

## 入力モデル

  * `idealmodel`: 理想モデル。`nothing`の場合、入力JSONから理想モデルを解析します。
  * `mixing`: 温度と体積の混合モデル。
  * `departure`: 出発モデル

## 説明

複数成分の経験的EoSモデルをインスタンス化します。`Rgas`は、プロパティ計算中に使用される気体定数の値を設定するために使用できます。

`coolprop_userlocations`がtrueの場合、Clapeyronは流体がCoolPropライブラリに存在するかどうかを確認しようとします。

`estimate_pure`がtrueの場合、JSONが見つからない場合、純粋モデルが`XiangDeiters`モデルを使用して推定されます。

`estimate_mixing`は、`AsymmetricMixing`を使用する場合に欠落している混合値を埋めるために使用されます。他の混合モデルでは効果がありません。

  * `estimate_mixing = :off`は、混合パラメータの計算を行わず、欠落している値が見つかった場合はエラーをスローします。
  * `estimate_mixing = :lb`は、欠落している混合パラメータのローレンツ-ベルテロット推定を行います。（γT = βT = γv = βv = 1.0）。さらに、`k`および`l` BIPを使用するために`LorentzBerthelotMixing`を渡すことができます。
  * `estimate_mixing = :linear`は、欠落している混合パラメータに対してγTとγvの平均を行います。`T(x) = ∑xᵢTᵢ`および`V(x) = ∑xᵢVᵢ`。さらに、これを直接行うために`LinearMixing`を使用できます。

`Rgas`は、マルチフルイドで使用される気体定数の値を設定します。デフォルトは以下の通りです：

  * `Rgas`が指定されておらず、入力が単一成分モデルの場合、`Rgas`の値は流体のjsonファイルから取得されます。
  * `Rgas`が指定されておらず、入力が多成分モデルの場合、`Rgas`の値は`Clapeyron.R̄ = Rgas() = 8.31446261815324`（2019年に定義された定数値）に設定されます。

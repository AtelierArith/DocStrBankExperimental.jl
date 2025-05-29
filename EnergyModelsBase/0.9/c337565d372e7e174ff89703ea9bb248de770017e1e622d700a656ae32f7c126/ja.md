```
abstract type AbstractElement
```

抽象要素は、エネルギーシステムの構成要素を形成する `EnergyModelsBase` のコアタイプに対応します。

# 導入された要素

  * **[`Node`](@ref)s** は、導入された [`Resource`](@ref)s を通じて定義されたエネルギーまたは質量を変換する技術に対応します。
  * **[`Link`](@ref)s** は、異なるノード間で [`Resource`](@ref)s を輸送します。

!!! tip "追加のAbstractElement"
    新しい要素を導入することが可能です。これらの要素は、新しい変数や制約も導入することができます。


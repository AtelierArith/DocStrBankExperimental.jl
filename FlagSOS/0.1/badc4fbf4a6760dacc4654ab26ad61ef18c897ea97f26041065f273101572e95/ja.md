```
QuadraticModule{T <: Flag, U <: Flag, B <: AbstractFlagModel{U, N, D}, N, D} <: AbstractFlagModel{T, N, D}
```

不等式のための二次モジュールを実装します。`FlagModel`のサブモデルとして使用されることを意図しています。`baseModel`のすべての要素を`inequality`で乗算し、それらを型`T`（例えば、ラベルを外すことによって）に変換します。不等式`f >= 0`は、`f`を記述する`QuantumFlag{U}`の形で与えられます。問題に不等式`f >= 0`と`-f >= 0`の両方が現れる場合、`EqualityModule`を使用する方が同等ですが、はるかに効率的です。

# パラメータ

  * `T`: ターゲットフラグタイプ
  * `U`: 不等式のフラグタイプ、およびベースモデルのターゲットタイプ
  * `B`: ベースモデルのタイプ
  * `N`: 制限パラメータ、`AbstractFlagModel`を参照
  * `D`: 最終最適化問題の係数のデータ型

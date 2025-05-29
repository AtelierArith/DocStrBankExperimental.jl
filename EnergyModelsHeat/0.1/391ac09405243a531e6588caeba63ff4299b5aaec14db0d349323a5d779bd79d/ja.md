```
HeatExchanger
```

`HeatExchanger`ノードは、他のプロセスからの「生」の余剰エネルギーを、地区暖房ネットワークで使用できる「利用可能な」エネルギーに変換します。

デフォルトの熱交換器は、熱伝達を最適化するために質量流が異なる可能性があると仮定しています。これは、型パラメータ`HeatExchangerAssumptions`によってエンコードされています。デフォルト値は`DifferentMassFlows`であり、代わりに`EqualMassFlows`を指定して、2つの回路での等しい質量流に制限することができます。

# フィールド

  * **`id`**はノードの名前/識別子です。
  * **`cap::TimeProfile`**は設置された容量です。
  * **`opex_var::TimeProfile`**は生産されたエネルギー単位あたりの変動運営費です。
  * **`opex_fixed::TimeProfile`**は固定運営費です。
  * **`input::Dict{<:Resource, <:Real}`**は変換値`Real`を持つ入力`Resource`です。
  * **`output::Dict{<:Resource, <:Real}`**は変換値`Real`を持つ生成された`Resource`です。
  * **`data::Vector{Data}`**は追加データ（例：投資用）です。フィールド`data`はコンストラクタの使用によって条件付きです。
  * **`delta_t_min`**は熱交換器のΔT_minです。

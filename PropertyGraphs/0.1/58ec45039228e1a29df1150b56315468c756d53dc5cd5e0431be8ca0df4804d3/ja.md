```
Edge(source::UInt, target::UInt, type::AbstractString, properties::Config)
```

プロパティグラフにおけるエッジを表します。

# フィールド

  * `source::UInt`: ソースノードの一意の識別子。
  * `target::UInt`: ターゲットノードの一意の識別子。
  * `type::AbstractString`: エッジのタイプまたはラベル。
  * `properties::Config`: エッジに関連付けられたプロパティ（キー-バリューのペア）を表す`Config`オブジェクト。

# コンストラクタ

  * `Edge(src::Integer, tgt::Integer, type::AbstractString; props...)`: 指定された`src`および`tgt`ノードID（`UInt`に変換）を持つ`Edge`を作成するための便利なコンストラクタで、`type`とオプションの`props`が`Config`コンストラクタに渡されます。
  * `Edge(src::UInt, tgt::UInt, type::AbstractString; props...)`: 指定された`src`および`tgt`ノードID、`type`、およびオプションの`props`を持つ`Edge`を作成するための便利なコンストラクタで、`props`は`Config`コンストラクタに渡されます。

# 例

```julia
Edge(1, 2, "friend"; since=2010)
```

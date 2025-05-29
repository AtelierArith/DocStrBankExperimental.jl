```
struct SemanticMeta <: DeviceLayout.Meta
    layer::Symbol
    index::Int = 1
    level::Int = 1
end
SemanticMeta(layer::String; kwargs...)
SemanticMeta(meta::Meta; kwargs...)
```

オブジェクトのレイヤー情報と属性のDeviceLayoutネイティブ表現。

セマンティックメタデータは、固定されたエンコーディングに言及することなく、要素の意味を指します。たとえば、「このポリゴンは地面の負の部分にある」はセマンティックですが、「このポリゴンはGDSレイヤー1、データタイプ2にある」はセマンティックではありません。セマンティックメタデータは、レイアウトが`CoordinateSystem`から特定の出力形式（たとえば、GDSII用の`Cell`）に対応する表現に変換される最終的な`render`ステップで使用されます。`render!(cell::Cell{S}, cs::CoordinateSystem; map_meta = identity, kwargs...)`への呼び出しは、`map_meta`関数を使用して各`GeometryEntity`のメタデータを`GDSMeta`にマッピングします。

`level`および`index`フィールドは、DeviceLayoutによって厳密な解釈が課されていません。（この意味では、GDSの`datatype`に似ています。）推奨される使用法は次のとおりです：

  * `index`は、レイヤー内の番号付きインスタンスを区別します。たとえば、グレースケールリソグラフィーやポート番号付けにおいて
  * `level`は、異なるコンテキストで発生するレイヤーのインスタンスを区別します。たとえば、同等のレイヤーが複数のレベルに存在する3Dスタック内で

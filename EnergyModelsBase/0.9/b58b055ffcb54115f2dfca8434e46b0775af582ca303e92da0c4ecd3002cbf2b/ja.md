```
constraints_capacity_installed(m, n::Node, 𝒯::TimeStructure, modeltype::EnergyModel)
constraints_capacity_installed(m, n::Storage, 𝒯::TimeStructure, modeltype::EnergyModel)
constraints_capacity_installed(m, l::Link, 𝒯::TimeStructure, modeltype::EnergyModel)
```

インストールされた容量に対する制約を作成するための関数。

これらの関数は、特定の `Node` または `Link` に対して他の方法が指定されていない場合のフォールバックオプションとして機能します。

!!! danger "この関数のディスパッチ"
    この関数は、投資を提供するために modeltype に対してディスパッチするためだけに使用されるべきです。新しい容量変数を作成する場合（ストレージノードの場合のように）、この関数と対応するノードタイプのメソッドを含めることが有益です。


```
is_unidirectional(l::Link)
```

リンク `l` が双方向で使用できるか、または一方向のみで使用できるかの論理値を返します。

!!! note "リンクにおける双方向フロー"
    現在の段階では、`EnergyModelsBase` にはフローの反転が可能な双方向で使用できるリンクは含まれていません。

    双方向フローを使用する予定がある場合は、これをサポートする独自のノードとリンクを宣言する必要があります。その後、この関数をディスパッチして組み込むことができます。


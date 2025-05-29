```
findlead!(panel::PanelStructure, l::Integer=1)
```

`panel`のすべてのid-timeの組み合わせに対して`l`番目のリード値のインデックスのベクトルを構築し、結果を`panel.laginds`に保存します。リード値が存在しない場合、そのインデックスは0で埋められます。詳細は[`ilead!`](@ref)を参照してください。

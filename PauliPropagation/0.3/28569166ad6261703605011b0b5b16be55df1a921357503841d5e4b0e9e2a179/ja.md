```
hardwareefficientcircuit(nqubits::Integer, nlayers::Integer; topology=nothing)
```

単一量子ビットのX-Z-XパウリゲートとYYエンタングリングゲートの層からなるハードウェア効率的な回路を作成します。トポロジーは量子ビットインデックスのペアのリストとして指定できます。トポロジーが指定されていない場合は、ブリックレイヤートポロジーが使用されます。

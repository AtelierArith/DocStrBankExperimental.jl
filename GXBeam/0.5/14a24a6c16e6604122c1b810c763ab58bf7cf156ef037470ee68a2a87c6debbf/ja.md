```
write_vtk(name, assembly::Assembly, [state::AssemblyState, ]λ::Number,
    eigenstate::AssemblyState; scaling=1.0, mode_scaling=1.0, cycles=1,
    steps=100)
```

`assembly`の弾性的な動きに対応する一連のファイルを作成します。これは、固有値`λ`で定義された変形状態`state`にエンコードされた状態と、固有ベクトル`eigenstate`にエンコードされた状態に基づいています。指定された時間期間にわたって行われます。

定常状態の変位は`scaling`でスケーリングでき、固有モードの変位は`mode_scaling`を使用してスケーリングできます。

現在の時間はメタデータタグ「time」にエンコードされています。

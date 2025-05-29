```
compliance_element(n::EMB.Node)
compliance_element(n::Storage)
compliance_element(l::Link)
```

それぞれの個別テスト関数のテストに対応するエラーと警告の2つの`NamedTuple`を返します。呼び出されるテスト関数は選択されたタイプに依存します：

!!! note "Node"
    次の関数が呼び出されます：

      * [`compliance_capacity`](@ref)、`Storage`ノードには適用されません、
      * [`compliance_opex_var`](@ref)、`Storage`ノードには適用されません、
      * [`compliance_opex_fixed`](@ref)、`Storage`ノードには適用されません、
      * [`compliance_inputs`](@ref)、ノードに入力がある場合、関数[`has_input`](@extref EnergyModelsBase.has_input)を通じて確認されます、
      * [`compliance_outputs`](@ref)、ノードに出力がある場合、関数[`has_output`](@extref EnergyModelsBase.has_output)を通じて確認されます、
      * [`compliance_data`](@ref)、
      * `Storage`ノードに対する[`compliance_level`](@ref)、`level`が[`AbstractStorageParameters`](@extref EnergyModelsBase.AbstractStorageParameters)に対応していることを確認するチェックを含み、
      * `Storage`ノードに対する[`compliance_stor_res`](@ref)。


!!! tip "Link"
    `Link`は`Node`よりも柔軟です。その結果、アクセス関数が機能しているかどうかは確認しません。代わりに、`Link`がフィールド`:from`と`:to`を持っているか、どちらかがnに制限されているかが確認されます。


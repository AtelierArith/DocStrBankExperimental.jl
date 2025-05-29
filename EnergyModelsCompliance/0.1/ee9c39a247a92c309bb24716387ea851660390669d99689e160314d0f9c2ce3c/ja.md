```
test_case(n::Source, 𝒯::TimeStructure, warn_log; co2::ResourceEmit = ResourceEmit("CO₂", 1.0))
test_case(n::NetworkNode, 𝒯::TimeStructure, warn_log; co2::ResourceEmit = ResourceEmit("CO₂", 1.0))
test_case(n::Storage, 𝒯::TimeStructure, warn_log; co2::ResourceEmit = ResourceEmit("CO₂", 1.0))
test_case(n::Sink, 𝒯::TimeStructure, warn_log; co2::ResourceEmit = ResourceEmit("CO₂", 1.0))
```

デフォルトのテストセットは、開発された [`Node`](@extref EnergyModelsBase.Node) `n` が `EnergyModelsBase` モデルに含まれることができ、結果として得られるモデルが解決可能であることをテストします。

テストセットは、与えられたノード構造に対して最小限の作業ケースを自動的に特定し、このケースを解決します。例の [`Source`](@extref EnergyModelsBase.Source) ノードは、すべてのバージョンで（ソースノードをテストする場合を除いて）OPEXが0の変数を持っています。これは、固定需要のない [`Sink`](@extref EnergyModelsBase.Sink) ノードをテストする場合、エネルギーをシンクノードに供給することが有益であるようにパラメータを提供する必要があることを意味します。これは、利益を得ることによって達成できます。

出力のない [`Storage`](@extref EnergyModelsBase.Storage) ノードの場合も同様です。

次のデフォルト値が選択されます：

  * [`capacity`](@extref EnergyModelsBase.capacity) 関数を使用できない場合、容量は100とします。それ以外の場合、容量はノードの容量に対して十分です。
  * [`opex_var`](@extref EnergyModelsBase.opex_var) 関数を使用できない場合（`n::Sink` を除くすべてのケースで）、シンクのペナルティを計算するために2500であると仮定します。

!!! warning "関数に関する潜在的な問題"
      * ストレージの充電または放電変数を固定するために `JuMP.fix` を使用する場合、新しい `has_input` または `has_output` のメソッドを提供しない限り、いくつかのテストが失敗する可能性があります。これらの関数は、この場合、ソースまたはシンクの `:cap_use` に関連しています。また、`:stor_charge_use` または `:stor_discharge_use` にも関連しています。
      * ノードへの `input` として co2 キーワード引数を持つ場合、関数は正しく機能しません。
      * 関数は、リンクされたノードの必要なシーケンスを評価するために設計されていません。たとえば、CCS レトロフィットは、2つのノードの直接的な結合を必要とします。これは一般化できません。
      * リンクに使用することはできません。なぜなら、`Node` を `:from` および `:to` フィールドの値として提供する必要があるからです。


# 引数

  * **`n::EMB.Node`** はテストされるノードです。
  * **`𝒯::TimeStructure`** は選択された時間構造です。単一の戦略的期間のみを含むべきです。
  * **`warn_log`** は、関数 `compliance_element` を呼び出すことによって得られる警告 `NamedTuple` です。

# キーワード引数

  * **`co2::ResourceEmit`** はモデル内のCO₂リソースです。ノードにCO₂が含まれていない場合は、指定する必要はありません。

# テスト

  * 最適化問題は最適解に至ります。
  * すべての接続ノードの変数 `:cap_use` は、少なくとも1つの時間期間で0.1を超えています。

!!! tip "Source, NetworkNode, and Sink"
    さらにテストします：

      * ノード `n` の変数 `:cap_use` は、少なくとも1つの時間期間で0.1を超えています。


!!! note "Storage"
    `Storage` ノードは、ランダムなソース変数OPEXと固定シンク需要を使用して、ストレージレベルの変化を分析します。これは、`Storage` ノードに出力がない場合、`Resource` を保存することが有益であることが重要であることを意味します。これは、負のOPEX項を通じて達成されなければなりません。さらにテストします：

      * ノード `n` の変数 `:stor_level`、`:stor_charge_use`、および `:stor_discharge_use` は、少なくとも1つの時間期間で0.1を超えています。


```

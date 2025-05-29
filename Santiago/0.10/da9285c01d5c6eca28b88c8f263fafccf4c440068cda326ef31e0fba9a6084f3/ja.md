```julia
select_systems(
    systems::Array{Santiago.System},
    n_select::Int64;
    target,
    maximize,
    selection_type,
    techs_include,
    techs_exclude,
    templates_include,
    templates_exclude
) -> Vector{Santiago.System}

```

最大 `n_select` システムのサブセットを選択します。この関数は、良好なターゲット値を持つシステムを特定することを目的としています。

ほとんどのシステムプロパティはターゲットとして使用できます。最も一般的に使用されるのは `sysappscore` です。

## 引数

  * `n_select::Int` 選択するシステムの数（可能な場合）
  * `target = "sysappscore"` システムをランク付けするために使用される値。`"sysappscore"`、`"connectivity"`、または `"ntechs"` のようなシステムプロパティの名前を含む文字列である必要があります。質量流量統計の場合は、製品と質量流量統計のペアである必要があります（例：`("phosphor" => "recovery_ratio")`）。
  * `maximize::Bool = true` `true` の場合、最も大きな `target` 値を持つシステムが選択されます。`false` の場合は最小のもの。
  * `selection_type = "diverse"` `"diverse"` または `"ranking"` のいずれかである必要があります。`"ranking"` の場合、最も大きい（または最も小さい）ターゲット値を持つシステムが返されます。`"diverse"` の場合、返されるシステムは大きい（または小さい）ターゲット値を持ちますが、できるだけ多様性もあります。多様性は主にシステムテンプレートによって決まります。

以下のオプション引数を使用して、選択をさらに制限することができます：

  * `techs_include`
  * `techs_exclude`
  * `templates_include`
  * `templates_exclude`

テンプレートは、最初の数文字だけを指定することで省略できます。*すべて*の一致するテンプレートが使用されます。これはインタラクティブな使用に便利ですが、混乱を招く可能性があります！たとえば、完全なテンプレート名 `"T1 basic template"` を提供する代わりに、略称 `"T1"` を使用できます。ただし、これにより `"T11 complicated template"` という名前のテンプレートにも一致します！したがって、略称が一意であることを確認してください。この例では、少なくとも `"T1 "` を使用する必要があります。

## 詳細

特別な機能として、引数 `target` は `"all"` と質量流量統計のペアも受け入れます。たとえば、`("all" => "recovery_ratio")` のように。この場合、すべての4つの製品にわたる質量流量統計の*平均*がターゲットとして使用されます。ただし、これはほとんどの質量流量統計には意味がないことに注意してください！

この関数は、入力システムにプロパティを追加する場合があります！以下のプロパティのいずれかが不足している場合は追加される可能性があります：

  * `template`
  * `sysappscore`
  * `ntech`
  * `connectivity`

```
AutoEnzyme{M,A}
```

自動微分のために[Enzyme.jl](https://github.com/EnzymeAD/Enzyme.jl)バックエンドを選択するために使用される構造体。

[ADTypes.jl](https://github.com/SciML/ADTypes.jl)によって定義されています。

# コンストラクタ

```
AutoEnzyme(; mode::M=nothing, function_annotation::Type{A}=Nothing)
```

# 型パラメータ

  * `A`は、微分する関数`f`がEnzymeに渡される方法を決定します。次のように設定できます：

      * 特定の注釈を強制するために`EnzymeCore.Annotation`のサブタイプ（`EnzymeCore.Const`や`EnzymeCore.Duplicated`など）
      * `Nothing`は単に`f`を渡し、Enzymeが最も適切な注釈を選択できるようにします

# フィールド

  * `mode::M`は自動微分モード（前方または逆）を決定します。次のように設定できます：

      * 特定のモードが必要な場合は`EnzymeCore.Mode`のサブタイプのオブジェクト（`EnzymeCore.Forward`や`EnzymeCore.Reverse`など）
      * 最適なモードを自動的に選択するために`nothing`

データセットを一意に識別するために使用できる説明。

ターゲットデータセットを説明するために使用される4つのフィールド：

  * `collection`、コレクションの名前またはUUID（オプション）。
  * `dataset`、データセットの名前またはUUID。
  * `type`、データセットからロードする必要があるタイプ。
  * `parameters`、一致する必要があるデータセットの追加パラメータ。

# コンストラクタ

```julia
Identifier(collection::Union{AbstractString, UUID, Nothing},
           dataset::Union{AbstractString, UUID},
           type::Union{QualifiedType, Nothing},
           parameters::SmallDict{String, Any})
```

# パース

Identifierは、次の形式の文字列として表現でき、オプションのコンポーネントは角括弧で囲まれます：

```
[COLLECTION:]DATASET[::TYPE]
```

このような形式は、単に`parse`関数を呼び出すことでIdentifierにパースできます。つまり、`parse(Identifier, "mycollection:dataset")`のようにします。

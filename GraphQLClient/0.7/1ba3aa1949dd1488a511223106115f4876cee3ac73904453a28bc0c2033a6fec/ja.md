```
introspect_object([client::Client],
                  object_name;
                  force=false,
                  reset_all=false,
                  parent_type=nothing,
                  parent_map=Dict{String, Type}(),
                  mutable=true,
                  allowed_level=2,
                  custom_scalar_types=Dict{String, DataType}())
```

オブジェクトを調査し、Julia型を作成します。

GraphQLスキーマによる再帰が可能なため、この調査は難しい場合があります。このドキュメントを注意深くお読みください。

# 親タイプ

すべての調査された型は、デフォルトで親タイプ `AbstractIntrospectedStruct` が与えられます。調査されるトップレベルオブジェクトの親タイプは `parent_type` で設定でき、調査される任意のオブジェクトの親タイプは `parent_map` 辞書を使用して設定できます。`object_type` が `parent_map` のキーであり、`parent_type` が `nothing` でない場合、`parent_type` の値が優先されます。

# StructTypes

`AbstractIntrospectedStruct` には、JSONシリアル化のための `Struct` の定義された `StructType` があります。調査される具体的な型のために `StructType` を定義するには、次のようにします。

```
StructTypes.StructType(::Type{GraphQLClient.get_introspected_object(object_name)}) = StructTypes.Struct()
```

# 再帰

再帰は2つのメソッドで処理されます。

1. `allowed_level` キーワード引数を提供して、調査の深さを制御します。
2. 現在調査中のオブジェクトのリストを維持します。オブジェクトは二度調査されることはできず、型は自分自身が定義されるまで型定義に使用できません。したがって、この状況が発生した場合、まだ定義されていない型を使用する必要があるフィールドは無視されます。これは、オブジェクトが調査される順序が最終的な構造体に影響を与える可能性があることを意味します。

例えば、次のオブジェクトを考えてみましょう。

```
Country:
 - name: String
 - leader: Person

Person:
 - name: String
 - countryOfBirth: Country
```

最初に `Country` を調査した場合、`Person` オブジェクトには `countryOfBirth` フィールドが含まれません。なぜなら、そのフィールドの型を `Country` に設定することは、その型が自分自身で定義される前には不可能だからです。最初に `Person` を調査した場合、同じ理由で `Country` オブジェクトには `leader` フィールドが含まれません。

# キーワード引数

  * `force=false`: `false` の場合、調査は既に調査された型をオブジェクトに使用します。`true` の場合、以前に調査された型は、`object_name` を調査している間に調査されると上書きされます。注意して使用してください。他の型が上書きされる型に依存している可能性があります。
  * `reset_all`: 調査されたすべての型を削除して、クリーンな状態から始めます。
  * `parent_type=nothing`: 新しい調査された構造体に与える親タイプ。上記のコメントを参照してください。
  * `parent_map=Dict{String, Type}()`: オブジェクト名を希望する親タイプにマッピングする辞書。`parent_type` が提供されている場合、この値は `object_name` の `parent_map` のエントリよりも優先されます。
  * `mutable=true`: トップレベルおよびすべての下位レベル型の可変性を設定するためのブール値。
  * `allowed_level=2`: 許可される調査のレベル数。例えば、これが `1` の場合、オブジェクトであるトップレベルフィールドのみが調査された型に含まれます。
  * `custom_scalar_types`: カスタムGraphQLスカラー型をJulia型にマッピングする辞書。このキーワード引数は、カスタムスカラー型が正しい型に調査されることを可能にします。

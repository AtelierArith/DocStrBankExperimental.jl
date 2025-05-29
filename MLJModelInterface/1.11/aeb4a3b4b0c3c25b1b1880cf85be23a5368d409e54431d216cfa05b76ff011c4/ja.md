```
is_same_except(m1, m2, exceptions::Symbol...; deep_properties=Symbol[])
```

もし `m1` と `m2` が `MLJType` の場合、次の条件がすべて満たされるなら `true` を返し、そうでなければ `false` を返します：

  * `typeof(m1) === typeof(m2)`
  * `propertynames(m1) === propertynames(m2)`
  * `exceptions` としてリストされているプロパティや `AbstractRNG` にバインドされているプロパティを除いて、各対応するプロパティ値のペアは「等しい」か、両方が未定義である。 （プロパティが `propertyname` として現れるが `fieldname` としては現れない場合、それは常に定義されていると見なされます。）

「等しい」という意味はプロパティ値の型によって異なります：

  * 自身が `MLJType` である値は、例外なしで `is_same_except` の意味で等しい場合に「等しい」と見なされます。
  * `MLJType` でない値は、`==` で等しい場合に「等しい」と見なされます。

「深い」プロパティの特別なケースでは、「等しい」の意味が異なります；詳細については [`deep_properties`](@ref) を参照してください。

もし `m1` または `m2` が `MLJType` オブジェクトでない場合、`==(m1, m2)` を返します。 ```

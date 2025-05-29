```
get_regex(r::RemoteConcept{<:AbstractAttributeType})
```

AttributeTypesが値の型Stringを持つ場合、受信する文字列がパターンを満たすことを証明するために正規表現パターンを設定することが可能です。そうでない場合、挿入は失敗します。この関数は、設定されている場合に正規表現文字列を返します。正規表現文字列はJavaプログラミング言語の規約に従います。

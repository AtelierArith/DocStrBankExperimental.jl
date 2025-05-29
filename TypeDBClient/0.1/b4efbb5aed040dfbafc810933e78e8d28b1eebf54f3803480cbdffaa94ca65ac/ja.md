```
set_regex(r::RemoteConcept{<:AbstractAttributeType},
    regex::Optional{AbstractString})
```

AttributeTypesが値の型Stringを持つ場合、受信する文字列がパターンに一致するかを確認するためにregexパターンを設定することが可能です。そうでない場合、挿入は失敗します。この関数は、指定された属性にregex文字列を設定します。regex文字列はJavaプログラミング言語の規約に従います。

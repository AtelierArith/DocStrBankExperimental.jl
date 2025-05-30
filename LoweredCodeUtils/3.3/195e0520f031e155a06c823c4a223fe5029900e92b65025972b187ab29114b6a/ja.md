```
lines_required!(isrequired::AbstractVector{Bool}, src::CodeInfo, edges::CodeEdges;
                norequire = ())
```

`lines_required`と同様ですが、`isrequired[idx]`が評価する必要があるすべてのステートメントに対してすでに`true`に設定されている場合です。他のすべてのステートメントは、エントリ時に`false`としてマークされるべきです。戻り値では、必要なステートメントの完全なセットが`true`としてマークされます。

`norequire`キーワード引数は、要件としてマークされるべきでないステートメント（`Int`のイテレータとして表される）を指定します。たとえば、メソッドシグネチャを抽出して新しい定義を評価しない場合は、`norequire = LoweredCodeUtils.exclude_named_typedefs(src, edges)`を使用します。

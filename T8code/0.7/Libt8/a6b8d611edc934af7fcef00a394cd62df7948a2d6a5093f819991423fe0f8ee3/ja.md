```
t8_element_array_t
```

[`t8_element_array_t`](@ref) は、特定の eclass*scheme 実装の [`t8*element_t`](@ref) * を格納するための配列です。これは sc*array*t のラッパーです。t8*element*array*t の関数によって新しい要素が作成されるたびに、要素のために eclass 関数 t8*element*new または t8*element*init が呼び出されます。したがって、t8*element*array*t の各要素は自動的に適切に初期化されます。

| フィールド  | 注釈                     |
|:------ |:---------------------- |
| scheme | 要素が格納されるべき eclass スキーム |
| array  | 要素が格納される配列             |

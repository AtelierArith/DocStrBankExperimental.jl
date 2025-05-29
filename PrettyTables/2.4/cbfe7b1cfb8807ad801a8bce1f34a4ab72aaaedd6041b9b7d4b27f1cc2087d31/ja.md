```
pretty_table_with_conf(conf::PrettyTablesConf, args...; kwargs...) -> Nothing
```

`conf`のデフォルト設定を使用して`pretty_table`を呼び出します。`args...`と`kwargs...`は`pretty_tables`に渡されるものと同じである可能性があります。`kwargs...`内のすべての設定は`conf`内のものを上書きします。

オブジェクト`conf`は、キーワードパラメータが以下に示す`pretty_table`関数によってサポートされる任意のものである`set_pt_conf`関数によって作成できます。
